---
title: 自訂 My 中可用的物件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: c0b47521c6a62071466ae4193cd8553bdfb3dcde
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890367"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>自訂 My 中可用的物件 (Visual Basic)

本主題說明您如何控制哪些`My`物件會藉由設定您的專案啟用`_MYTYPE`條件式編譯常數。 Visual Studio 整合式開發環境 (IDE) 會保留`_MYTYPE`專案與專案類型的同步處理的條件式編譯常數。  
  
## <a name="predefined-mytype-values"></a>預先定義的\_MYTYPE 的值  

您必須使用`/define`編譯器選項來設定`_MYTYPE`條件式編譯常數。 指定您自己的值時`_MYTYPE`常數，您必須括住的字串值反斜線/引號 (\\") 序列。 例如，您可以使用：  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 下表顯示哪些`_MYTYPE`條件式編譯常數設定為幾個專案類型。  
  
|專案類型|\_MYTYPE 的值|  
|------------------|--------------------|  
|類別庫|"Windows"|  
|主控台應用程式|「 主控台 」|  
|Web|「 Web 」|  
|Web 控制項程式庫|「 WebControl"|  
|Windows 應用程式|"WindowsForms"|  
|Windows 應用程式，當從自訂 `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Windows 控制項程式庫|"Windows"|  
|Windows 服務|「 主控台 」|  
|Empty|「 空白 」|  
  
> [!NOTE]
> 所有的條件式編譯的字串比較會區分大小寫，不論`Option Compare`陳述式設定。  
  
## <a name="dependent-my-compilation-constants"></a>相依\_我編譯常數  

`_MYTYPE`條件式編譯常數，控制的其他幾個值`_MY`編譯常數：  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_PHOTOS.CONTOSO.COM|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|「 主控台 」|「 主控台 」|"Windows"|未定義|"Windows"|true|  
|「 自訂 」|未定義|未定義|未定義|未定義|未定義|  
|「 空白 」|未定義|未定義|未定義|未定義|未定義|  
|「 Web 」|未定義|「 Web 」|false|「 Web 」|false|  
|「 WebControl"|未定義|「 Web 」|false|「 Web 」|true|  
|"Windows"或""|"Windows"|"Windows"|未定義|"Windows"|true|  
|"WindowsForms"|"WindowsForms"|"Windows"|true|"Windows"|true|  
|"WindowsFormsWithCustomSubMain"|「 主控台 」|"Windows"|true|"Windows"|true|  
  
 根據預設，未定義的條件式編譯常數會解析成`FALSE`。 編譯您的專案覆寫預設行為時，您可以指定為未定義的常數的值。  
  
> [!NOTE]
> 當`_MYTYPE`設定為"Custom"，此專案包含`My`命名空間，但它不包含的物件。 不過，設定`_MYTYPE`到 「 空白 」 可防止編譯器加入`My`命名空間和其物件。  
  
 下表描述的預先定義的值影響`_MY`編譯的常數。  
  
|常數|意義|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|可讓`My.Application`，如果此常數位於 「 主控台 」 的 Windows，"或"WindowsForms 」:<br /><br /> -「 主控台 」 版本衍生自<xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>。 具有較少的成員，比 「 Windows 」 版本。<br />-「 Windows 」 版本衍生自<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>並具有較少的成員，比"WindowsForms 」 版本。<br />-「 WindowsForms"新版`My.Application`衍生自<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>。 如果`TARGET`常數定義為 「 winexe"，則此類別包含`Sub Main`方法。|  
|`_MYCOMPUTERTYPE`|可讓`My.Computer`，如果常數是 「 Web 」 或 「 Windows 」:<br /><br /> -「 Web 」 版本衍生自<xref:Microsoft.VisualBasic.Devices.ServerComputer>，且具有較少的成員，比 「 Windows 」 版本。<br />-"Windows"新版`My.Computer`衍生自<xref:Microsoft.VisualBasic.Devices.Computer>。|  
|`_MYFORMS`|可讓`My.Forms`，如果此常數位於`TRUE`。|  
|`_MYUSERTYPE`|可讓`My.User`，如果常數是 「 Web 」 或 「 Windows 」:<br /><br /> -「 Web 」 版本`My.User`目前 HTTP 要求的使用者身分識別與相關聯。<br />版本-"Windows"`My.User`執行緒的目前主體相關聯。|  
|`_MYWEBSERVICES`|可讓`My.WebServices`，如果此常數位於`TRUE`。|  
|`_MYTYPE`|可讓`My.Log`， `My.Request`，和`My.Response`，如果常數是 「 Web 」。|  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My 如何相依於專案類型](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms 物件](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response 物件](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices 物件](../../../visual-basic/language-reference/objects/my-webservices-object.md)
