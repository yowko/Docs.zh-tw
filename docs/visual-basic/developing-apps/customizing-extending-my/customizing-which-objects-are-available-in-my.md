---
title: 自訂 My 中可用的物件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: caddad463f7c525c8b715d70f49bf8bebcc7cfbd
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701256"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>自訂 My 中可用的物件 (Visual Basic)

本主題描述如何藉由設定專案的 @no__t 1 條件式編譯常數，來控制要啟用哪些 @no__t 0 物件。 Visual Studio 的整合式開發環境（IDE）會讓專案的 `_MYTYPE` 條件式編譯常數與專案的類型保持同步。  
  
## <a name="predefined-_mytype-values"></a>預先定義的 \_MYTYPE 值  

您必須使用 `/define` 編譯器選項來設定 `_MYTYPE` 條件式編譯常數。 為 `_MYTYPE` 常數指定您自己的值時，您必須將字串值括在反斜線/引號（\\）序列中。 例如，您可以使用：  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 下表顯示針對數個專案類型，@no__t 0 的條件式編譯常數設定為。  
  
|專案類型|\_MYTYPE 值|  
|------------------|--------------------|  
|類別庫|時段|  
|主控台應用程式|控制|  
|Web|網路|  
|Web 控制項程式庫|WebControl|  
|Windows 應用程式|WindowsForms|  
|Windows 應用程式（以自訂 `Sub Main` 開始）|"WindowsFormsWithCustomSubMain"|  
|Windows 控制項程式庫|時段|  
|Windows 服務|控制|  
|Empty|空|  
  
> [!NOTE]
> 所有條件式編譯字串的比較都會區分大小寫，不論如何設定 `Option Compare` 的語句。  
  
## <a name="dependent-_my-compilation-constants"></a>相依 \_MY 編譯常數  

@No__t 0 的條件式編譯常數則會控制數個其他 @no__t 1 個編譯常數的值：  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|控制|控制|時段|未定義|時段|true|  
|客戶|未定義|未定義|未定義|未定義|未定義|  
|空|未定義|未定義|未定義|未定義|未定義|  
|網路|未定義|網路|false|網路|false|  
|WebControl|未定義|網路|false|網路|true|  
|"Windows" 或 ""|時段|時段|未定義|時段|true|  
|WindowsForms|WindowsForms|時段|true|時段|true|  
|"WindowsFormsWithCustomSubMain"|控制|時段|true|時段|true|  
  
 根據預設，未定義的條件式編譯常數會解析為 `FALSE`。 您可以在編譯專案時指定未定義常數的值，以覆寫預設行為。  
  
> [!NOTE]
> 當 `_MYTYPE` 設定為 "Custom" 時，專案會包含 @no__t 1 命名空間，但不包含任何物件。 不過，將 `_MYTYPE` 設定為 "Empty"，會使編譯器無法加入 @no__t 1 命名空間及其物件。  
  
 下表描述 @no__t 0 編譯常數的預先定義值的效果。  
  
|常數|意義|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|啟用 `My.Application`，如果常數為 "Console"、"Windows" 或 "WindowsForms"：<br /><br /> -"Console" 版本衍生自 <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>。 和的成員數目少於 "Windows" 版本。<br />-"Windows" 版本衍生自 @no__t 4.9.0-，而且具有少於 "WindowsForms" 版本的成員。<br />-@No__t-0 的 "WindowsForms" 版本衍生自 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>。 如果 @no__t 0 常數定義為 "winexe"，則類別會包含 `Sub Main` 方法。|  
|`_MYCOMPUTERTYPE`|啟用 `My.Computer`，如果常數是 "Web" 或 "Windows"：<br /><br /> -「Web」版本衍生自 <xref:Microsoft.VisualBasic.Devices.ServerComputer>，而且具有比「Windows」版本少的成員。<br />-@No__t-0 的 "Windows" 版本衍生自 <xref:Microsoft.VisualBasic.Devices.Computer>。|  
|`_MYFORMS`|如果常數 `TRUE`，則啟用 `My.Forms`。|  
|`_MYUSERTYPE`|啟用 `My.User`，如果常數是 "Web" 或 "Windows"：<br /><br /> -@No__t-0 的「Web」版本與目前 HTTP 要求的使用者識別相關聯。<br />-@No__t-0 的 "Windows" 版本與執行緒目前的主體相關聯。|  
|`_MYWEBSERVICES`|如果常數 `TRUE`，則啟用 `My.WebServices`。|  
|`_MYTYPE`|啟用 `My.Log`、`My.Request` 和 `My.Response` （如果常數為 "Web"）。|  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My 如何相依於專案類型](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/define （Visual Basic）](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms 物件](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response 物件](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices 物件](../../../visual-basic/language-reference/objects/my-webservices-object.md)
