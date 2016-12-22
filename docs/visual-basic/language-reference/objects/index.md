---
title: "Objects (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "objects [Visual Basic]"
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Objects (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

本主題提供其他主題的連結，而這些主題將會說明 Visual Basic 執行階段物件，並含有其成員程序、屬性和事件的表格。  
  
## Visual Basic 執行階段物件  
  
|||  
|-|-|  
|<xref:Microsoft.VisualBasic.Collection>|提供非常方便的方式，可將一組相關的項目視為單一物件。|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|包含與執行階段錯誤有關的資訊。|  
|`My.Application` 物件包含下列類別：<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> 提供可在所有專案中使用的成員。<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 提供可在 Windows Form 應用程式中使用的成員。<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> 提供可在主控台應用程式中使用的成員。|提供僅與目前應用程式或 DLL 關聯的資料。  不可使用 `My.Application` 變更系統層級的資訊。<br /><br /> 部分成員只有 Windows Form 或主控台應用程式才能使用。|  
|`My.Application.Info` \(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>\)|提供取得應用程式相關資訊的屬性，例如版本號碼、描述、已載入組件等。|  
|`My.Application.Log` \(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>\)|提供一個屬性和多個方法，將事件和例外狀況資訊寫入應用程式的記錄檔接聽程式。|  
|`My.Computer` \(<xref:Microsoft.VisualBasic.Devices.Computer>\)|提供用於管理電腦元件 \(例如，音效、時鐘、鍵盤、檔案系統等\) 的屬性。|  
|`My.Computer.Audio` \(<xref:Microsoft.VisualBasic.Devices.Audio>\)|提供用於播放音效的方法。|  
|`My.Computer.Clipboard` \(<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>\)|提供管理 \[剪貼簿\] 的方法。|  
|`My.Computer.Clock` \(<xref:Microsoft.VisualBasic.Devices.Clock>\)|提供用於從系統時鐘存取目前本機時間和全球定位時間 \(Universal Coordinated Time\) \(相當於格林威治標準時間 \(Greenwich Mean Time\)\) 的屬性。|  
|`My.Computer.FileSystem` \(<xref:Microsoft.VisualBasic.FileIO.FileSystem>\)|提供用於處理磁碟機、檔案和目錄的屬性和方法。|  
|`My.Computer.FileSystem.SpecialDirectories` \(<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>\)|提供用於存取常用參考目錄的屬性。|  
|`My.Computer.Info` \(<xref:Microsoft.VisualBasic.Devices.ComputerInfo>\)|提供用於取得電腦記憶體、已載入組件、名稱和作業系統之資訊的屬性。|  
|`My.Computer.Keyboard` \(<xref:Microsoft.VisualBasic.Devices.Keyboard>\)|提供用於存取鍵盤目前狀態 \(例如，目前按下的是哪個鍵\) 的屬性，並提供將按鍵傳送至使用中視窗的方法。|  
|`My.Computer.Mouse` \(<xref:Microsoft.VisualBasic.Devices.Mouse>\)|提供的屬性可取得安裝在本機電腦上滑鼠之格式與組態的相關資訊。|  
|`My.Computer.Network` \(<xref:Microsoft.VisualBasic.Devices.Network>\)|提供用於與電腦所連接之網路互動的屬性、事件和方法。|  
|`My.Computer.Ports` \(<xref:Microsoft.VisualBasic.Devices.Ports>\)|提供用於存取電腦序列埠的屬性和方法。|  
|`My.Computer.Registry` \(<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>\)|提供用於管理登錄的屬性和方法。|  
|[My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)|提供可用於存取目前專案中所宣告之每個 Windows Form 執行個體的屬性。|  
|`My.Log` \(<xref:Microsoft.VisualBasic.Logging.AspLog>\)|提供 Web 應用程式的一個屬性和多個方法，將事件和例外狀況資訊寫入應用程式的記錄檔接聽程式。|  
|[My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)|取得所要求網頁的 <xref:System.Web.HttpRequest> 物件。  `My.Request` 物件會包含目前 HTTP 要求的相關資訊。<br /><br /> `My.Request` 物件只能用於 [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] 應用程式。|  
|[My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md)|提供屬性和類別，用以存取應用程式的資源。|  
|[My.Response Object](../../../visual-basic/language-reference/objects/my-response-object.md)|取得與 <xref:System.Web.UI.Page> 相關聯的 <xref:System.Web.HttpResponse> 物件。  這個物件允許您傳送 HTTP 回應資料給用戶端，並包含該回應的資訊。<br /><br /> `My.Response` 物件只能用於 [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] 應用程式。|  
|[My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md)|提供存取應用程式之設定的屬性和方法。|  
|`My.User` \(<xref:Microsoft.VisualBasic.ApplicationServices.User>\)|提供目前使用者相關資訊的存取。|  
|[My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)|提供屬性，這些屬性可用於建立並存取目前專案所參考之每個 Web 服務的單一執行個體。|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|提供用於剖析結構化文字檔的方法和屬性。|  
  
## 請參閱  
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)   
 [Visual Basic](../../../visual-basic/index.md)