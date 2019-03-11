# How to store struct in redis the right way

If you want to store a struct in redis, you can always convert it into bytes and then store it, something like this

```
dataBytes := json.Marshal(r)
r.Set(key, dataBytes, 0)
```
 and then while retrieving the struct back, you will get the string form of the data which you can convert back to your struct
 
 ```
 res, err := r.Get(key).Result()
 if err != nil {
  //Do something
  return
 }
 err := json.Unmarshal([]byte(res), &r)
 ```
 
 This works fine, but there is a better way of doing it, what you can do is implement encoding package's **MarshalBinary** and **UnmarshalBinary** interface functions
 
 ```
 //MarshalBinary - Used to store struct in redis
func (r *Response) MarshalBinary() (data []byte, err error) {
	return json.Marshal(r)
}

// UnmarshalBinary - Used to retrieve struct from redis
func (r *Response) UnmarshalBinary(data []byte) error {
	return json.Unmarshal(data, &r)
}
 ```
 
 Now what this allows you to do is send the struct implementing this response directly to redis and convert the response returned by redis in a much more readable way
 
 ```
 r.Set(key, &response, 0)
 
 res, err := r.Get(key).Result()
 err = response.UnmarshalBinary([]byte(s))
 ```
 
 You don't need have the intermediate dataBytes like in the first case, and the UnmarshalBinary is just plus point
