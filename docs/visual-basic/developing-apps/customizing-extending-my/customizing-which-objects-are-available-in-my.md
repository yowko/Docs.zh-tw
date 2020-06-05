---
title: 自訂 My 可以使用的物件
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: 5245c129281bc8c7c1c6fe9215a221889380a901
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410214"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>自訂 My 中可用的物件 (Visual Basic)

本主題描述如何藉 `My` 由設定專案的 `_MYTYPE` 條件式編譯常數，來控制要啟用哪些物件。 Visual Studio 的整合式開發環境（IDE）會讓 `_MYTYPE` 專案的條件式編譯常數與專案的類型保持同步。  
  
## <a name="predefined-_mytype-values"></a>預先定義的 \_ MYTYPE 值  

您必須使用 `/define` 編譯器選項來設定 `_MYTYPE` 條件式編譯常數。 為常數指定您自己的值時 `_MYTYPE` ，您必須將字串值括在反斜線/引號（ \\ "）序列中。 例如，您可以使用：  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 下表顯示 `_MYTYPE` 數個專案類型的條件式編譯常數設定。  
  
|專案類型|\_MYTYPE 值|  
|------------------|--------------------|  
|類別庫|"Windows"|  
|主控台應用程式|控制|  
|Web|網路|  
|Web 控制項程式庫|WebControl|  
|Windows 應用程式|WindowsForms|  
|Windows 應用程式（從自訂開始）`Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Windows 控制項程式庫|"Windows"|  
|Windows 服務|控制|  
|空白|空|  
  
> [!NOTE]
> 所有條件式編譯字串的比較都會區分大小寫，不論語句的 `Option Compare` 設定方式為何。  
  
## <a name="dependent-_my-compilation-constants"></a>相依于 \_ 我的編譯常數  

`_MYTYPE`接著，條件式編譯常數會控制數個其他編譯常數的值 `_MY` ：  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|控制|控制|"Windows"|未定義|"Windows"|TRUE|  
|客戶|未定義|未定義|未定義|未定義|未定義|  
|空|未定義|未定義|未定義|未定義|未定義|  
|網路|未定義|網路|FALSE|網路|FALSE|  
|WebControl|未定義|網路|FALSE|網路|TRUE|  
|"Windows" 或 ""|"Windows"|"Windows"|未定義|"Windows"|TRUE|  
|WindowsForms|WindowsForms|"Windows"|TRUE|"Windows"|TRUE|  
|"WindowsFormsWithCustomSubMain"|控制|"Windows"|TRUE|"Windows"|TRUE|  
  
 根據預設，未定義的條件式編譯常數會解析為 `FALSE` 。 您可以在編譯專案時指定未定義常數的值，以覆寫預設行為。  
  
> [!NOTE]
> 當 `_MYTYPE` 設定為 "Custom" 時，專案會包含 `My` 命名空間，但不包含任何物件。 不過，將設 `_MYTYPE` 為 "Empty" 可防止編譯器加入 `My` 命名空間及其物件。  
  
 下表描述編譯常數預先定義值的效果 `_MY` 。  
  
|持續性|意義|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|`My.Application`如果常數為 "Console"、"Windows" 或 "WindowsForms"，則會啟用：<br /><br /> -「主控台」版本衍生自 <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> 。 和的成員數目少於 "Windows" 版本。<br />-"Windows" 版本衍生自 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> 。和的成員數目少於 "WindowsForms" 版本。<br />-的 "WindowsForms" 版本 `My.Application` 衍生自 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 。 如果 `TARGET` 常數定義為 "winexe"，則類別會包含 `Sub Main` 方法。|  
|`_MYCOMPUTERTYPE`|`My.Computer`如果常數是 "Web" 或 "Windows"，則會啟用：<br /><br /> -「Web」版本衍生自 <xref:Microsoft.VisualBasic.Devices.ServerComputer> ，而且具有比「Windows」版本還要少的成員。<br />-的 "Windows" 版本 `My.Computer` 衍生自 <xref:Microsoft.VisualBasic.Devices.Computer> 。|  
|`_MYFORMS`|`My.Forms`如果常數為，則啟用 `TRUE` 。|  
|`_MYUSERTYPE`|`My.User`如果常數是 "Web" 或 "Windows"，則會啟用：<br /><br /> -的「Web」版本 `My.User` 與目前 HTTP 要求的使用者識別相關聯。<br />-的 "Windows" 版本 `My.User` 與執行緒目前的主體相關聯。|  
|`_MYWEBSERVICES`|`My.WebServices`如果常數為，則啟用 `TRUE` 。|  
|`_MYTYPE`|如果常數為「Web」，則啟用 `My.Log` 、 `My.Request` 和 `My.Response` 。|  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My 與專案類型的相依關係](../development-with-my/how-my-depends-on-project-type.md)
- [條件式編譯](../../programming-guide/program-structure/conditional-compilation.md)
- [-define （Visual Basic）](../../reference/command-line-compiler/define.md)
- [My.Forms 物件](../../language-reference/objects/my-forms-object.md)
- [My.Request 物件](../../language-reference/objects/my-request-object.md)
- [My.Response 物件](../../language-reference/objects/my-response-object.md)
- [My.WebServices 物件](../../language-reference/objects/my-webservices-object.md)
