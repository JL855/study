# study
go进阶课程笔记

http库的使用
  //Body和GetBody：重点在于Body是一次性的，而GetBody默认情况下是nil，一般中间件会考虑注入方法（gin）
  
  func readBodyOnce(w http.ResponseWriter, r *http.Request) {
	//只能读一次
	body, err := io.ReadAll(r.Body)
	if err != nil {
		fmt.Fprintf(w, "read body failed: %v",err)
		return
	}
	fmt.Fprintf(w, "read the data: %s\n", string(body))
}

  //URL：注意URL里面的字段的含义可能并不如你期望的那样
  
  //Form：记得调用前先用ParseForm，别忘了请求里面加上http头
  
  func form(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "before parse form %v\n", r.Form)
	err := r.ParseForm()
	if err != nil {
		fmt.Fprintf(w, "parse form error: %v\n",r.Form)
	}
	fmt.Fprintf(w, "after parse form %v\n", r.Form)
}
  

