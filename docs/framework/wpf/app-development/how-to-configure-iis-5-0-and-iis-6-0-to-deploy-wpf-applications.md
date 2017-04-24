---
title: "如何：設定 IIS 5.0 和 IIS 6.0 以部署 WPF 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "調整內容到期日設定"
  - "應用程式, 部署"
  - "設定 Web 伺服器部署 WPF 應用程式"
  - "內容到期日設定, 調整"
  - "部署應用程式"
  - "副檔名, 註冊"
  - "MIME 類型, 註冊"
  - "註冊副檔名"
  - "註冊 MIME 類型"
  - "Web 伺服器, 設定部署 WPF 應用程式"
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：設定 IIS 5.0 和 IIS 6.0 以部署 WPF 應用程式
您可以從大部分的 Web 伺服器部署 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式，只要伺服器是以適當的 [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] 類型設定的。  根據預設，[!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] 是以這些 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型設定的，但 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 和 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] 則不是。  
  
 本主題說明如何設定 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 和 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] 以部署 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
   
  
> [!NOTE]
>  您可以在登錄中檢查 *UserAgent* 字串，判斷系統是否安裝有 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]。  如需詳細資訊和檢查用於判斷系統是否有安裝 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 的 *UserAgent* 字串的指令碼，請參閱 [偵測有無安裝 .NET Framework 3.0](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)。  
  
<a name="content_expiration"></a>   
## 調整內容到期日設定  
 您應該將內容到期日設定調整為 1 分鐘。  下列程序概述如何使用 [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] 執行此項作業。  
  
1.  按一下 \[**開始**\] 功能表，指向 \[**系統管理工具**\]，然後按一下 \[**網際網路資訊服務 \(IIS\) 管理員**\]。  您也可以從命令列使用 "%SystemRoot%\\system32\\inetsrv\\iis.msc" 啟動這個應用程式。  
  
2.  展開 [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] 樹狀目錄，直到找到 \[**預設的網站**\] 節點。  
  
3.  以滑鼠右鍵按一下 \[**預設的網站**\]，並從內容功能表選取 \[**屬性**\]。  
  
4.  選取 \[**HTTP 標頭**\] 索引標籤，並按一下 \[啟用內容到期日\]。  
  
5.  設定內容於 1 分鐘後到期。  
  
<a name="register_mime_types"></a>   
## 註冊 MIME 類型和副檔名  
 您必須註冊數種 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型和副檔名，這樣用戶端系統上的瀏覽器可以載入正確的處理常式。  您需要加入下列類型：  
  
|副檔名|MIME 類型|  
|---------|-------------|  
|.manifest|application\/manifest|  
|.xaml|application\/xaml\+xml|  
|.application|application\/x\-ms\-application|  
|.xbap|application\/x\-ms\-xbap|  
|.deploy|application\/octet\-stream|  
|.xps|application\/vnd.ms\-xpsdocument|  
  
> [!NOTE]
>  您不需要在用戶端系統上註冊 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型或副檔名。  這些在安裝 [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] 時即會自動註冊。  
  
 下列 [!INCLUDE[TLA#tla_visualbscrpt](../../../../includes/tlasharptla-visualbscrpt-md.md)] 範例會自動將必要的 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型加入到 [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]。  若要使用指令碼，複製程式碼成伺服器上的 .vbs 檔案。  然後，從命令列執行該檔案，或在 [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)] 中按兩下檔案，即可執行指令碼。  
  
```  
' This script adds the necessary Windows Presentation Foundation MIME types   
' to an IIS Server.  
' To use this script, just double-click or execute it from a command line.  
' Running this script multiple times results in multiple entries in the IIS MimeMap.  
  
Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec  
Const ADS_PROPERTY_UPDATE = 2   
  
' Set the MIME types to be added  
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _  
    "application/xaml+xml", ".application", "application/x-ms-application", _  
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _  
    ".xps", "application/vnd.ms-xpsdocument")   
  
' Get the mimemap object   
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")  
  
' Call AddMimeType for every pair of extension/MIME type  
For counter = 0 to UBound(MimeTypesToAddArray) Step 2  
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)  
Next  
  
' Create a Shell object  
Set WshShell = CreateObject("WScript.Shell")  
  
' Stop and Start the IIS Service  
Set oExec = WshShell.Exec("net stop w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = WshShell.Exec("net start w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = Nothing  
  
' Report status to user  
WScript.Echo "Windows Presentation Foundation MIME types have been registered."  
  
' AddMimeType Sub  
Sub AddMimeType (Ext, MType)  
  
    ' Get the mappings from the MimeMap property.   
    MimeMapArray = MimeMapObj.GetEx("MimeMap")   
  
    ' Add a new mapping.   
    i = UBound(MimeMapArray) + 1   
    Redim Preserve MimeMapArray(i)   
    Set MimeMapArray(i) = CreateObject("MimeMap")   
    MimeMapArray(i).Extension = Ext   
    MimeMapArray(i).MimeType = MType   
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray  
    MimeMapObj.SetInfo  
  
End Sub  
```  
  
> [!NOTE]
>  多次執行這個指令碼，會在 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 或 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] Metabase 中建立多個 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 對應項目。  
  
 執行這個指令碼後，可能不會從 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 或 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)] 看到其他的 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型。  然而，這些 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型已經加入到 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 或 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] Metabase。  下列指令碼會顯示 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 或 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] Metabase 中的所有 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型。  
  
```  
' This script lists the MIME types for an IIS Server.  
' To use this script, just double-click or execute it from a command line   
' by calling cscript.exe  
  
dim mimeMapEntry, allMimeMaps  
  
' Get the mimemap object.  
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")  
allMimeMaps = mimeMapEntry.GetEx("MimeMap")  
  
' Display the mappings in the table.  
For Each mimeMap In allMimeMaps  
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")  
Next  
```  
  
 將指令碼儲存為 `.vbs` 檔案 \(例如 `DiscoverIISMimeTypes.vbs`\)，並從命令提示字元使用下列命令執行指令碼：  
  
 `cscript DiscoverIISMimeTypes.vbs`