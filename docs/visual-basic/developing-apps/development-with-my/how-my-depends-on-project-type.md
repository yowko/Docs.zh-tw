---
title: My 如何相依於專案類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 49efaa6470b6fea062be0663d8b1c48b9284bd99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671989"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>My 如何相依於專案類型 (Visual Basic)
`My` 只有在特定專案類型所需的物件公開 （expose)。 比方說，`My.Forms`物件是在 Windows Forms 應用程式中可用的但無法使用主控台應用程式中。 本主題描述其中`My`物件都在不同的專案類型。  
  
## <a name="my-in-windows-applications-and-web-sites"></a>我在 Windows 應用程式和網站  
 `My` 公開可用於目前的專案類型; 的物件它會隱藏不適用的物件。 例如下, 圖顯示`My`Windows Forms 專案中的物件模型。  
  
 ![圖形的我的 Windows Forms 應用程式中](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 在網站專案中，`My`公開的 Web 開發人員相關的物件 (例如`My.Request`並`My.Response`物件) 同時隱藏不相關的物件 (例如`My.Forms`物件)。 下圖顯示`My`網站專案中的物件模型：  
  
 ![圖形的我的 Web 應用程式](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>專案詳細資料  
 下表顯示哪些`My`物件會啟用預設為八個專案類型：Windows 應用程式、 類別程式庫、 主控台應用程式、 Windows 控制項程式庫、 Web 控制項程式庫、 Windows 服務、 空的和網站。  
  
 有三種版本`My.Application`物件、 兩個版本`My.Computer`物件，以及兩個版本`My.User`物件; 註腳會提供有關這些版本的詳細資料表格之後。  
  
|我的物件|Windows 應用程式|類別庫|主控台應用程式|Windows 控制項程式庫|Web 控制項程式庫|Windows 服務|Empty|網站|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**[是]** <sup>1</sup>|**[是]** <sup>2</sup>|**[是]** <sup>3</sup>|**[是]** <sup>2</sup>|否|**[是]** <sup>3</sup>|否|否|  
|`My.Computer`|**[是]** <sup>4</sup>|**[是]** <sup>4</sup>|**[是]** <sup>4</sup>|**[是]** <sup>4</sup>|**[是]** <sup>5</sup>|**[是]** <sup>4</sup>|否|**[是]** <sup>5</sup>|  
|`My.Forms`|**是**|否|否|**是**|否|否|否|否|  
|`My.Log`|否|否|否|否|否|否|否|**是**|  
|`My.Request`|否|否|否|否|否|否|否|**是**|  
|`My.Resources`|**是**|**是**|**是**|**是**|**是**|**是**|否|否|  
|`My.Response`|否|否|否|否|否|否|否|**是**|  
|`My.Settings`|**是**|**是**|**是**|**是**|**是**|**是**|否|否|  
|`My.User`|**[是]** <sup>6</sup>|**[是]** <sup>6</sup>|**[是]** <sup>6</sup>|**[是]** <sup>6</sup>|**[是]** <sup>7</sup>|**[是]** <sup>6</sup>|否|**[是]** <sup>7</sup>|  
|`My.WebServices`|**是**|**是**|**是**|**是**|**是**|**是**|否|否|  
  
 <sup>1</sup> Windows Form 版本`My.Application`。 衍生自主控台版本 （請參閱註 3）;新增應用程式的 windows 與互動的支援，並提供 Visual Basic 應用程式模型。  
  
 <sup>2</sup>程式庫版本`My.Application`。 提供應用程式所需的基本功能： 提供成員撰寫的應用程式記錄及存取應用程式資訊。  
  
 <sup>3</sup>主控台版本`My.Application`。 衍生自程式庫版本 （請參閱註 2），並新增其他成員來存取應用程式的命令列引數和 ClickOnce 部署資訊。  
  
 <sup>4</sup>的 Windows 版本`My.Computer`。 衍生自伺服器版本 （請參閱註 5），並在用戶端電腦上，例如鍵盤、 螢幕和滑鼠提供有用的物件的存取。  
  
 <sup>5</sup>的伺服器版本`My.Computer`。 提供的電腦，例如名稱、 存取權的時鐘，等等的基本資訊。  
  
 <sup>6</sup>的 Windows 版本`My.User`。 這個物件是執行緒的目前的身分識別與相關聯。  
  
 <sup>7</sup>的 web 版本`My.User`。 這個物件是應用程式的目前 HTTP 要求的使用者身分識別與相關聯。  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [自訂 My 中可用的物件](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms 物件](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response 物件](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices 物件](../../../visual-basic/language-reference/objects/my-webservices-object.md)
