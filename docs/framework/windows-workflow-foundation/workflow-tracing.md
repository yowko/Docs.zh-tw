---
title: "工作流程追蹤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 工作流程追蹤
工作流程追蹤提供使用 .NET Framework 追蹤接聽程式擷取診斷資訊的方式。如果偵測到應用程式的問題，可以啟用追蹤，等到問題解決再停用追蹤。您可以運用兩種方式啟用工作流程的偵錯追蹤。您可以使用事件追蹤檢視器加以設定，也可以使用 <xref:System.Diagnostics>，將追蹤事件傳送至檔案。  
  
## 啟用 ETW 中的偵錯追蹤  
 若要使用 ETW 啟用追蹤，請啟用事件檢視器中的偵錯通道：  
  
1.  巡覽至事件檢視器中的分析與偵錯記錄檔。  
  
2.  在事件檢視器的樹狀結構檢視中，巡覽至 \[**事件檢視器\-\>應用程式與服務記錄檔\-\>Microsoft\-\>Windows\-\>應用程式伺服器\-應用程式**\]。以滑鼠右鍵按一下 \[**應用程式伺服器\-應用程式**\]，並且選取 \[**檢視\-\>顯示分析與偵錯記錄檔**\]。以滑鼠右鍵按一下 \[**偵錯**\] 並選取 \[**啟用記錄檔**\]。  
  
3.  當工作流程執行偵錯並將追蹤發出至 ETW 偵錯頻道時，即可在事件檢視器中檢視這些追蹤。巡覽至 \[**事件檢視器\-\>應用程式與服務記錄檔\-\>Microsoft\-\>Windows\-\>應用程式伺服器\-應用程式**\]。以滑鼠右鍵按一下 \[**偵錯**\] 並選取 \[**重新整理**\]。  
  
4.  預設的分析追蹤緩衝區大小只有 4 KB；建議您將大小增加至 32 KB。若要執行這項操作，請執行下列步驟。  
  
    1.  在目前的 Framework 目錄 \(例如 C:\\Windows\\Microsoft.NET\\Framework\\v4.0.21203\) 中執行下列命令：`wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2.  將 Windows.ApplicationServer.Applications.man 檔案中的 \<bufferSize\> 值變更為 32。  
  
        ```  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
  
        ```  
  
    3.  在目前的 Framework 目錄 \(例如 C:\\Windows\\Microsoft.NET\\Framework\\v4.0.21203\) 中執行下列命令：`wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
>  如果您使用 .NET Framework 4 Client Profile，則必須先從 .NET Framework 4 目錄執行下列命令註冊 ETW 資訊清單：`ServiceModelReg.exe –i –c:etw`  
  
## 啟用以 System.Diagnostics 進行偵錯追蹤  
 這些接聽程式可在工作流程應用程式的 App.config 檔案或工作流程服務的 Web.config 檔案中設定。此範例中設定了 [TextWriterTraceListener](http://go.microsoft.com/fwlink/?LinkId=165424)，將追蹤資訊儲存至目前目錄中的 MyTraceLog.txt 檔案。  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## 請參閱  
 [監控功能概念](http://go.microsoft.com/fwlink/?LinkId=201273)   
 [監控應用程式](http://go.microsoft.com/fwlink/?LinkId=201275)