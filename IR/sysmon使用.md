#### 安装
`sysmon -i`<br />安装服务和驱动
#### 卸载
`sysmon -u`<br />卸载服务和驱动
#### 指定规则文件安装
`sysmon -accepteula -i sysmonconfig-export.xml`
#### 更新配置
`sysmon -c sysmonconfig.export.xml`
#### 更改配置为默认配置
`sysmon -c --`
#### 显示配置架构
`sysmon -s`
#### 配置文件实例
```xml
<event name="SYSMON_RAWACCESS_READ" value="9" level="Informational "template="RawAccessRead detected" rulename="RawAccessRead" version="2">  
  <data name="UtcTime" inType="win:UnicodeString" outType="xs:string"/>  
  <data name="ProcessGuid" inType="win:GUID"/>  
  <data name="ProcessId" inType="win:UInt32" outType="win:PID"/>  
  <data name="Image" inType="win:UnicodeString" outType="xs:string"/>  
  <data name="Device" inType="win:UnicodeString" outType="xs:string"/>  
</event>  
```
监控DNS解析
```xml
<Sysmon schemaversion="4.21">
    <EventFiltering>
      <DnsQuery onmatch="exclude">
      </DnsQuery>
    </EventFiltering>
</Sysmon>
```
