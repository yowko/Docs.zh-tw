---
title: "Customizing Which Objects are Available in My (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "My namespace, customizing"
  - "My namespace"
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Customizing Which Objects are Available in My (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

本主題會描述如何為專案設定 `_MYTYPE` 條件式編譯常數，控制要啟動的 `My` 物件。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 整合式開發環境 \(IDE\) 會讓專案的 `_MYTYPE` 條件式編譯常數與專案的類型同步。  
  
## Predefined \_MYTYPE 值  
 您必須使用 `/define` 編譯器選項，設定 `_MYTYPE` 條件式編譯常數。  針對 `_MYTYPE` 常數指定自己的值時，必須以反斜線\/引號 \(\\"\) 的順序括住字串值。  例如，您可以使用：  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 此表會顯示針對數種專案類型而設定的 `_MYTYPE` 條件式編譯常數。  
  
|專案類型|\_MYTYPE 值|  
|----------|----------------|  
|類別庫|"Windows"|  
|主控台應用程式|"Console"|  
|Web|"Web"|  
|Web 控制項程式庫|"WebControl"|  
|Windows 應用程式|"WindowsForms"|  
|Windows 應用程式 \(以自訂的 `Sub Main` 啟動時\)|"WindowsFormsWithCustomSubMain"|  
|Windows 控制項程式庫|"Windows"|  
|Windows 服務|"Console"|  
|空白|"Empty"|  
  
> [!NOTE]
>  所有條件式編譯字串比較都區分大小寫，不管如何設定 `Option Compare` 陳述式 \(Statement\)。  
  
## Dependent \_MY 編譯常數  
 `_MYTYPE` 條件式編譯常數依序控制數個其他 `_MY` 編譯常數的值：  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Console"|"Console"|"Windows"|未定義|"Windows"|TRUE|  
|"Custom"|未定義|未定義|未定義|未定義|未定義|  
|"Empty"|未定義|未定義|未定義|未定義|未定義|  
|"Web"|未定義|"Web"|FALSE|"Web"|FALSE|  
|"WebControl"|未定義|"Web"|FALSE|"Web"|TRUE|  
|"Windows" 或 ""|"Windows"|"Windows"|未定義|"Windows"|TRUE|  
|"WindowsForms"|"WindowsForms"|"Windows"|TRUE|"Windows"|TRUE|  
|"WindowsFormsWithCustomSubMain"|"Console"|"Windows"|TRUE|"Windows"|TRUE|  
  
 根據預設，未定義的條件式編譯常數解析為 `FALSE`。  編譯您的專案覆寫預設行為時，可以為尚未定義的常數指定值。  
  
> [!NOTE]
>  當 `_MYTYPE` 設為 "Custom" 時，專案包含 `My` 命名空間 \(Namespace\)，但是它沒有包含任何物件。  不過，將 `_MYTYPE` 設定為 "Empty" 可以防止編譯器加入 `My` 命名空間和它的物件。  
  
 這個表格描述 `_MY` 編譯常數之預先定義值的作用。  
  
|常數|意義|  
|--------|--------|  
|`_MYAPPLICATIONTYPE`|如果常數為 "Console"、"Windows" 或 "WindowsForms"，啟用 `My.Application`：<br /><br /> -   "Console" 版本衍生自 <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>，  且成員數少於 "Windows" 版本。<br />-   "Windows" 版本衍生自 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>，且成員數少於 "WindowsForms" 版本。<br />-   `My.Application` 的 "WindowsForms" 版本衍生自 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>。  如果將 `TARGET` 常數定義為 "winexe"，則類別包括 `Sub Main` 方法。|  
|`_MYCOMPUTERTYPE`|如果常數為 "Web" 或 "Windows"，啟用 `My.Computer`：<br /><br /> -   "Web" 版本衍生自 <xref:Microsoft.VisualBasic.Devices.ServerComputer>，且成員數少於 "Windows" 版本。<br />-   `My.Computer` 的 "Windows" 版本衍生自 <xref:Microsoft.VisualBasic.Devices.Computer>。|  
|`_MYFORMS`|如果常數為 `TRUE`，啟用 `My.Forms`。|  
|`_MYUSERTYPE`|如果常數為 "Web" 或 "Windows"，啟用 `My.User`：<br /><br /> -   `My.User` 的 "Web" 版本與目前 HTTP 要求的使用者身分相關聯。<br />-   `My.User` 的 "Windows" 版本與執行緒目前的主體相關聯。|  
|`_MYWEBSERVICES`|如果常數為 `TRUE`，啟用 `My.WebServices`。|  
|`_MYTYPE`|如果常數為 "Web"，啟用 `My.Log`、`My.Request` 和 `My.Response`。|  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [My.Response Object](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)