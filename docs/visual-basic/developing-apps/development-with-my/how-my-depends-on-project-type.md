---
title: "我如何相依於專案類型 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d193dade94980f04b31605ea6fa968f9fa7d0ad6
ms.lasthandoff: 03/13/2017

---
# <a name="how-my-depends-on-project-type-visual-basic"></a>My 如何相依於專案類型 (Visual Basic)
`My`會公開特定專案類型所需的物件。 例如，`My.Forms`物件是在 Windows Form 應用程式中可用的但無法使用主控台應用程式中。 本主題描述這`My`物件都在不同的專案類型。  
  
## <a name="my-in-windows-applications-and-web-sites"></a>我在 Windows 應用程式和網站  
 `My`會公開可用於目前的專案類型; 的物件它會隱藏不適用的物件。 例如下, 圖顯示`My`Windows Form 專案中的物件模型。  
  
 ![圖形的我的 Windows Form 應用程式中](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 在網站專案中，`My`公開給 Web 程式開發人員與相關的物件 (例如`My.Request`和`My.Response`物件) 同時隱藏不相關的物件 (例如`My.Forms`物件)。 下圖顯示`My`網站專案中的物件模型︰  
  
 ![圖形的我的 Web 應用程式](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>專案詳細資料  
 下表顯示這`My`依預設會啟用物件，為八個專案類型︰ Windows 應用程式、 類別程式庫、 主控台應用程式、 Windows 控制項程式庫、 Web 控制項程式庫、 Windows 服務、 空的以及網站。  
  
 有三種版本`My.Application`物件時，兩個版本`My.Computer`物件，以及兩個版本的`My.User`物件; 註腳會提供有關這些版本的詳細資料表格之後。  
  
|我的物件|Windows 應用程式|類別庫|主控台應用程式|Windows 控制項程式庫|Web 控制項程式庫|Windows 服務|Empty|網站|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Yes** <sup>1</sup>|**Yes** <sup>2</sup>|**Yes** <sup>3</sup>|**Yes** <sup>2</sup>|否|**Yes** <sup>3</sup>|否|否|  
|`My.Computer`|**Yes** <sup>4</sup>|**Yes** <sup>4</sup>|**Yes** <sup>4</sup>|**Yes** <sup>4</sup>|**Yes** <sup>5</sup>|**Yes** <sup>4</sup>|否|**Yes** <sup>5</sup>|  
|`My.Forms`|**是**|否|否|**是**|否|否|否|否|  
|`My.Log`|否|否|否|否|否|否|否|**是**|  
|`My.Request`|否|否|否|否|否|否|否|**是**|  
|`My.Resources`|**是**|**是**|**是**|**是**|**是**|**是**|否|否|  
|`My.Response`|否|否|否|否|否|否|否|**是**|  
|`My.Settings`|**是**|**是**|**是**|**是**|**是**|**是**|否|否|  
|`My.User`|**Yes** <sup>6</sup>|**Yes** <sup>6</sup>|**Yes** <sup>6</sup>|**Yes** <sup>6</sup>|**Yes** <sup>7</sup>|**Yes** <sup>6</sup>|否|**Yes** <sup>7</sup>|  
|`My.WebServices`|**是**|**是**|**是**|**是**|**是**|**是**|否|否|  
  
 <sup>1</sup>的 Windows Form 版本`My.Application`。 從主控台版本中衍生 （請參閱註 3）。加入應用程式的 windows 與互動的支援，並提供[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]應用程式模型。  
  
 <sup>2</sup>程式庫版本`My.Application`。 提供應用程式所需的基本功能︰ 提供成員撰寫的應用程式記錄及存取應用程式資訊。  
  
 <sup>3</sup>主控台版本`My.Application`。 衍生自程式庫版本 （請參閱註 2），並加入其他成員存取應用程式的命令列引數和 ClickOnce 部署資訊。  
  
 <sup>4</sup>的 Windows 版本`My.Computer`。 衍生自伺服器版本 （請參閱註 5），並在用戶端電腦上，例如鍵盤、 螢幕和滑鼠提供有用的物件的存取。  
  
 <sup>5</sup>伺服器版本的`My.Computer`。 提供基本資訊的電腦，例如名稱、 存取時鐘，依此類推。  
  
 <sup>6</sup>的 Windows 版本`My.User`。 此物件目前的執行緒目前的身分識別相關聯。  
  
 <sup>7</sup>的 web 版本`My.User`。 這個物件是相關聯的應用程式的目前 HTTP 要求的使用者識別。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer></xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log></xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User></xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [自訂可用的物件在我](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)   
 [My.Forms 物件](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [My.Response 物件](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [My.WebServices 物件](../../../visual-basic/language-reference/objects/my-webservices-object.md)
