# A-SOUL-Dynamic-Reminder
正在重构并施工中，请暂时不要clone本仓库。

## 写在前面  
由于Google将于2023年停止对Manifest V2的支持，因此ADR需要重构代码并迁移至V3，该仓库存放Manifest V3版本的ADR源代码，V2版本请访问 https://github.com/Z-Bokle/A-SOUL-Dynamic-Reminder-V2

## 注意事项  
1.该插件在Windows 10 + Microsoft Edge平台上开发并测试，其他平台暂未做过测试，Chrome及使用其内核的浏览器理论上兼容；  
2.开启Edge的启动增强功能或在后台运行扩展设置以后，该插件可以在前台不打开浏览器的情况下继续工作，一旦插件功能启用，会发出一条h5通知提示；  
3.受限制于浏览器Alarm API限制，提醒功能可能会有若干分钟延迟，取决于浏览器上是否有其他插件或应用占用了这个API；  
4.插件没有运行环境检测功能，如果发现提醒功能延迟时间过长或无法工作，请先检查网络连接，再考虑反馈问题；  
5.不需要使用该插件或正在使用笔记本电脑的电池供电时，请进入插件管理页面手动关闭插件，受制于background的实现机制，暂时不能在插件中释放不需要的资源，插件的耗电情况未做相关测试。

## 更新记录
0.2.0  
重构代码，将manifest从V2更新至V3，并根据Google官方文档对插件运行机制进行修改  
- 将后台页面background更新为service_worker，由于service_worker无法直接操作DOM，引入jsdom第三方库以操作DOM；此外，由于jquery初始化时需要直接操作DOM，es6方式引入会导致service_worker注册失败，因此暂时弃用；
- 重写ajax相关代码，脱离jquery和XMLHttpRequest的限制，改用fetch()；
- 待定
