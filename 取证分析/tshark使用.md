### 基础使用
`-R ${filter}`  
读取时过滤器  
`-Y ${filter}`  
展示时过滤器  
`-n`  
禁止地址名字解析
`-w ${outfile}`
w数据的输出文件。这个参数不设置，tshark将会把解码结果输出到stdout,“-w -”表示把raw输出到stdout。如果要把解码结果输出到文件，使用重定向“>”而不要-w参数。 
`-F ${filetype}`
设置输出的文件格式，不加参数则显示支持的格式


### 规则
参考BPF表达式
### 例子
#### 抓包  
`tshark -i wlan0 -w out.pcap`  
#### 读取Pcap  
`tshark -r out.pcap`  
#### 只展示过滤后的数据  
`tshark -Y|--display-filter <fileter rule> -r out.pcap`  
#### 根据过滤规则抓包  
`tshark -f 'udp port 53'`  
#### 选择特定的字段输出  
`tshark -e http.request.method -e ip.src`  
#### 从数据包中提取http数据  
`tshark -nr out.pcap --export-objects http,${folder}` 