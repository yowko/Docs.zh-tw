---
title: My 與專案類型的相依關係
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 975b8feb001bcab22185be0a360b0512de099b79
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330273"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>My 如何相依於專案類型 (Visual Basic)

`My` 只會公開特定專案類型所需的物件。 例如，`My.Forms` 物件可在 Windows Forms 應用程式中使用，但無法在主控台應用程式中使用。 本主題描述哪些 `My` 物件可用於不同的專案類型。  
  
## <a name="my-in-windows-applications-and-web-sites"></a>我的 Windows 應用程式和網站  

 `My` 只會公開在目前專案類型中有用的物件;它會隱藏不適用的物件。 例如，下圖顯示 Windows Forms 專案中的 `My` 物件模型。  
  
 ![此圖顯示 Windows Forms 應用程式中的「我的物件模型」。](./media/how-my-depends-on-project-type/my-object-model-windows-forms.png)  
  
 在網站專案中，`My` 會公開與 Web 開發人員相關的物件（例如 `My.Request` 和 `My.Response` 物件），同時隱藏不相關的物件（例如 `My.Forms` 物件）。 下圖顯示網站專案中的 `My` 物件模型：  
  
 ![顯示 Web 應用程式中「我的物件模型」的圖表。](./media/how-my-depends-on-project-type/my-object-model-web.png)  
  
## <a name="project-details"></a>專案詳細資料  

 下表顯示預設會針對八個專案類型啟用哪些 `My` 物件： Windows 應用程式、類別庫、主控台應用程式、Windows 控制項程式庫、Web 控制項程式庫、Windows 服務、空白和網站。  
  
 `My.Application` 物件有三個版本、兩個版本的 `My.Computer` 物件，以及兩個 `My.User` 物件版本;如需這些版本的詳細資訊，請閱讀資料表後面的註腳。  
  
|我的物件|Windows 應用程式|類別庫|主控台應用程式|Windows 控制項程式庫|Web 控制項程式庫|Windows 服務|Empty|網站|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**是** <sup>1</sup>|**是** <sup>2</sup>|**是** <sup>3</sup>|**是** <sup>2</sup>|否|**是** <sup>3</sup>|否|否|  
|`My.Computer`|**是** <sup>4</sup>|**是** <sup>4</sup>|**是** <sup>4</sup>|**是** <sup>4</sup>|**是** <sup>5</sup>|**是** <sup>4</sup>|否|**是** <sup>5</sup>|  
|`My.Forms`|**是**|否|否|**是**|否|否|否|否|  
|`My.Log`|否|否|否|否|否|否|否|**是**|  
|`My.Request`|否|否|否|否|否|否|否|**是**|  
|`My.Resources`|**是**|**是**|**是**|**是**|**是**|**是**|否|否|  
|`My.Response`|否|否|否|否|否|否|否|**是**|  
|`My.Settings`|**是**|**是**|**是**|**是**|**是**|**是**|否|否|  
|`My.User`|**是** <sup>6</sup>|**是** <sup>6</sup>|**是** <sup>6</sup>|**是** <sup>6</sup>|**是** <sup>7</sup>|**是** <sup>6</sup>|否|**是** <sup>7</sup>|  
|`My.WebServices`|**是**|**是**|**是**|**是**|**是**|**是**|否|否|  
  
 <sup>1</sup> Windows Forms 版本的 `My.Application`。 衍生自主控台版本（請參閱注3）;新增與應用程式視窗互動的支援，並提供 Visual Basic 應用程式模型。  
  
 <sup>2</sup>程式庫版本的 `My.Application`。 提供應用程式所需的基本功能：提供寫入應用程式記錄檔和存取應用程式資訊的成員。  
  
 <sup>3</sup> `My.Application`的主控台版本。 衍生自程式庫版本（請參閱注2），並新增其他成員來存取應用程式的命令列引數和 ClickOnce 部署資訊。  
  
 <sup>4</sup> `My.Computer`的 Windows 版本。 衍生自伺服器版本（請參閱注5），並提供用戶端電腦上有用物件（例如鍵盤、螢幕和滑鼠）的存取權。  
  
 <sup>5</sup>伺服器版本的 `My.Computer`。 提供電腦的基本資訊，例如名稱、存取時鐘等等。  
  
 <sup>6</sup> Windows 版本的 `My.User`。 這個物件與執行緒目前的身分識別相關聯。  
  
 <sup>7</sup> Web 版本的 `My.User`。 此物件與應用程式目前 HTTP 要求的使用者識別相關聯。  
  
## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [自訂 My 中可用的物件](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-define （Visual Basic）](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms 物件](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response 物件](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices 物件](../../../visual-basic/language-reference/objects/my-webservices-object.md)
