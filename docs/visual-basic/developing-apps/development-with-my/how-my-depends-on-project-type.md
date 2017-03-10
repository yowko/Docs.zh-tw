---
title: "How My Depends on Project Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "_MYTYPE"
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How My Depends on Project Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`My` 只會公開 \(Expose\) 特定專案類型所需的物件。  例如，`My.Forms` 物件可用於 Windows Form 應用程式，但不能用於主控台應用程式 \(Console Application\)。  這個主題會描述哪些 `My` 物件可用於不同的專案類型。  
  
## Windows 應用程式和網站中的 My  
 `My` 只會公開在目前專案類型中有用的物件，並隱藏不適用的物件。  例如，下列影像會在 Windows Form 專案中顯示 `My` 物件模型 \(Object Model\)。  
  
 ![Windows Forms 應用程式中的 My 圖案](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 在網站專案中，`My` 隱藏不相關的物件 \(如 `My.Forms` 物件\) 時，會公開與 Web Developer 相關的物件 \(如 `My.Request` 和 `My.Response` 物件\)。  下列影像會在網站專案中顯示 `My` 物件模型：  
  
 ![Web 應用程式中的 My 圖案](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## 專案詳細資料  
 下表會顯示根據預設針對八個專案類型所啟用的 `My` 物件：Windows 應用程式、類別庫、主控台應用程式 \(Console Application\)、Windows 控制項程式庫、Web 控制項程式庫、Windows 服務、空白和網站。  
  
 有三個版本的 `My.Application` 物件、兩個版本的 `My.Computer` 物件和兩個版本的 `My.User` 物件，而表格後的註腳會提供這些版本的詳細資料。  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|My 物件|Windows 應用程式|類別庫|主控台應用程式|Windows 控制項程式庫|Web 控制項程式庫|Windows 服務|空白|網站|  
|`My.Application`|**有** <sup>1</sup>|**有** <sup>2</sup>|**有** <sup>3</sup>|**有** <sup>2</sup>|否|**有** <sup>3</sup>|否|否|  
|`My.Computer`|**有** <sup>4</sup>|**有** <sup>4</sup>|**有** <sup>4</sup>|**有** <sup>4</sup>|**有** <sup>5</sup>|**有** <sup>4</sup>|否|**有** <sup>5</sup>|  
|`My.Forms`|**是**|否|否|**是**|否|否|否|否|  
|`My.Log`|否|否|否|否|否|否|否|**是**|  
|`My.Request`|否|否|否|否|否|否|否|**是**|  
|`My.Resources`|**是**|**是**|**是**|**是**|**是**|**是**|否|否|  
|`My.Response`|否|否|否|否|否|否|否|**是**|  
|`My.Settings`|**是**|**是**|**是**|**是**|**是**|**是**|否|否|  
|`My.User`|**有** <sup>6</sup>|**有** <sup>6</sup>|**有** <sup>6</sup>|**有** <sup>6</sup>|**有** <sup>7</sup>|**有** <sup>6</sup>|否|**有** <sup>7</sup>|  
|`My.WebServices`|**是**|**是**|**是**|**是**|**是**|**是**|否|否|  
  
 <sup>1</sup> `My.Application` 的 Windows Form 版本。  從主控台版本中衍生 \(請參閱第 3 點\)、加入會與應用程式視窗互動的支援，並提供 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 應用程式模型。  
  
 <sup>2</sup> `My.Application` 的程式庫版本。  提供應用程式所需的基本功能：提供寫入應用程式記錄檔和存取應用程式資訊的成員。  
  
 <sup>3</sup> `My.Application` 的主控台版本。  從程式庫版本中衍生 \(請參閱第 2 點\)，並加入存取應用程式之命令列引數的其他成員，以及 ClickOnce 部署資訊。  
  
 <sup>4</sup> `My.Computer` 的 Windows 版本。  從伺服器版本中衍生 \(請參閱第 5 點\)，並提供對在用戶端機器上有用物件的存取，如鍵盤、螢幕和滑鼠。  
  
 <sup>5</sup> `My.Computer` 的伺服器版本。  提供有關電腦的基本資訊，如名稱、存取系統時鐘等。  
  
 <sup>6</sup> `My.User` 的 Windows 版本。  此物件會與執行緒的目前識別 \(Identity\) 相關。  
  
 <sup>7</sup> `My.User` 的 Web 版本。  此物件會與應用程式之目前 HTTP 要求的使用者身分相關。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [My.Response Object](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)