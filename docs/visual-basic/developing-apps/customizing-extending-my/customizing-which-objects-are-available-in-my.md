---
title: "自訂可用的物件在我 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My namespace, customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 6791398270e4348adf356eb36a385bfbefde873c
ms.lasthandoff: 03/13/2017

---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>自訂 My 中可用的物件 (Visual Basic)
本主題說明您如何控制哪些`My`會藉由設定您的專案啟用物件`_MYTYPE`條件式編譯常數。 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]整合式開發環境 (IDE) 會保留`_MYTYPE`專案與專案類型的同步處理的條件式編譯常數。  
  
## <a name="predefined-mytype-values"></a>預先定義的 _MYTYPE 值  
 您必須使用`/define`編譯器選項來設定`_MYTYPE`條件式編譯常數。 指定您自己的值時`_MYTYPE`常數，您必須括住的字串值反斜線/引號 (\\」) 序列。 例如，您可以使用︰  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 下表顯示哪些`_MYTYPE`條件式編譯常數會設定為針對數個專案類型。  
  
|專案類型|_MYTYPE 值|  
|------------------|--------------------|  
|類別庫|「 Windows 」|  
|主控台應用程式|「 主控台 」|  
|Web|[網頁]|  
|Web 控制項程式庫|「 WebControl 」|  
|Windows 應用程式|「 WindowsForms 」|  
|Windows 應用程式時使用的自訂啟動`Sub Main`|「 WindowsFormsWithCustomSubMain 」|  
|Windows 控制項程式庫|「 Windows 」|  
|Windows 服務|「 主控台 」|  
|Empty|「 空的 」|  
  
> [!NOTE]
>  所有的條件式編譯的字串比較會區分大小寫，不論`Option Compare`陳述式設定。  
  
## <a name="dependent-my-compilation-constants"></a>相依 _MY 編譯常數  
 `_MYTYPE`條件式編譯常數，控制的其他幾個值`_MY`編譯常數︰  
  
|_MYTYPE|_MYAPPLICATIONTYPE|_MYCOMPUTERTYPE|_MYFORMS|_MYUSERTYPE|_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|「 主控台 」|「 主控台 」|「 Windows 」|未定義|「 Windows 」|TRUE|  
|「 自訂 」|未定義|未定義|未定義|未定義|未定義|  
|「 空的 」|未定義|未定義|未定義|未定義|未定義|  
|[網頁]|未定義|[網頁]|FALSE|[網頁]|FALSE|  
|「 WebControl 」|未定義|[網頁]|FALSE|[網頁]|TRUE|  
|「 Windows 」 或 「 」|「 Windows 」|「 Windows 」|未定義|「 Windows 」|TRUE|  
|「 WindowsForms 」|「 WindowsForms 」|「 Windows 」|TRUE|「 Windows 」|TRUE|  
|「 WindowsFormsWithCustomSubMain 」|「 主控台 」|「 Windows 」|TRUE|「 Windows 」|TRUE|  
  
 根據預設，未定義的條件式編譯常數解析為`FALSE`。 編譯專案，以覆寫預設行為時，您可以指定未定義的常數的值。  
  
> [!NOTE]
>  當`_MYTYPE`設為"Custom"時，專案包含`My`命名空間，但它不包含的物件。 不過，設定`_MYTYPE`至"Empty"可以防止編譯器加入`My`命名空間及其物件。  
  
 下表描述的預先定義的值影響`_MY`編譯常數。  
  
|常數|意義|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|可讓`My.Application`，如果常數是 「 主控台 」 的 Windows 中，"或"WindowsForms":<br /><br /> -「 主控台 」 版本是衍生自<xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>。</xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> 而且沒有比 「 Windows 」 版本較少的成員。<br />為 「 Windows 」 版本是衍生自<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>也具有比 「 WindowsForms 」 版本較少的成員。</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase><br />-「 WindowsForms 」 版本`My.Application`衍生自<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>。</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 如果`TARGET`常數定義為 「 winexe 」，則該類別包含`Sub Main`方法。|  
|`_MYCOMPUTERTYPE`|可讓`My.Computer`，如果常數是 「 Web 」 或 「 Windows 」:<br /><br /> -[網頁] 版本是衍生自<xref:Microsoft.VisualBasic.Devices.ServerComputer>，且具有比 「 Windows 」 版本較少的成員。</xref:Microsoft.VisualBasic.Devices.ServerComputer><br />為 「 Windows 」 版本`My.Computer`衍生自<xref:Microsoft.VisualBasic.Devices.Computer>。</xref:Microsoft.VisualBasic.Devices.Computer>|  
|`_MYFORMS`|可讓`My.Forms`常數時， `TRUE`。|  
|`_MYUSERTYPE`|可讓`My.User`，如果常數是 「 Web 」 或 「 Windows 」:<br /><br /> 版本-"Web"`My.User`目前 HTTP 要求的使用者身分識別相關聯。<br />為 「 Windows 」 版本`My.User`執行緒的目前主體相關聯。|  
|`_MYWEBSERVICES`|可讓`My.WebServices`常數時， `TRUE`。|  
|`_MYTYPE`|可讓`My.Log`， `My.Request`，和`My.Response`，如果常數是 「 Web 」。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer></xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log></xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User></xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [我如何的專案類型而定](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)   
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)   
 [My.Forms 物件](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [My.Response 物件](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [My.WebServices 物件](../../../visual-basic/language-reference/objects/my-webservices-object.md)
