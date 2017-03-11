---
title: "/errorreport | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-errorreport compiler option [Visual Basic]"
  - "/errorreport compiler option [Visual Basic]"
  - "errorreport compiler option [Visual Basic]"
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# /errorreport
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器應如何報告編譯器內部錯誤。  
  
## 語法  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## 備註  
 這個選項提供便利的方式，向 Microsoft 的 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 團隊報告 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 內部編譯器錯誤 \(ICE\)。  編譯器預設並不會將任何資訊傳送給 Microsoft。  然而，如果真的遇到編譯器內部錯誤，則這個選項可以讓您向 Microsoft 報告錯誤。  該資訊會協助 Microsoft 工程師找出原因，也有助於改善下一版 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)]。  
  
 使用者是否能夠傳送報告，完全是依電腦和使用者的原則權限而定。  
  
 下表彙總 `/errorreport` 選項的效果。  
  
|||  
|-|-|  
|選項|行為|  
|`prompt`|如果發生編譯器內部錯誤，則會出現對話方塊，您就可以檢視編譯器所收集的實際資料。  可以判斷錯誤報告中是否有任何敏感性資訊，並決定是否將它傳送給 Microsoft。  如果決定傳送，而且機器和使用者原則設定也都允許的情況下，則編譯器會將資料傳送給 Microsoft。|  
|`queue`|將錯誤報告排成佇列。  當您以系統管理員權限登入時，您可以報告自上次登入後的任何失敗 \(傳送失敗報告的提示不會超過每三天一次\)。  如果沒有指定 `/errorreport` 選項，這就是預設行為。|  
|`send`|如果發生編譯器內部錯誤，且機器和使用者原則設定也都允許的情況下，則編譯器會將資料傳送給 Microsoft。<br /><br /> `/errorReport:send` 選項會嘗試將錯誤資訊自動傳送給 Microsoft。  這個選項取決於登錄。  如需在登錄中設定適當值的詳細資訊，請參閱[如何在 Visual Studio 2008 命令列工具中開啟自動錯誤報告](http://go.microsoft.com/fwlink/?LinkID=184695) \(英文\)。|  
|`none`|如果發生編譯器內部錯誤，則不會進行收集或傳送給 Microsoft。|  
  
 編譯器傳送的資料包含發生錯誤時的堆疊，並且通常包含一些原始程式碼。  如果將 `/errorreport` 與 [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) 選項搭配使用，則會傳送整個原始程式檔。  
  
 這個選項最好是與 [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) 選項搭配使用，因為它會讓 Microsoft 工程師更容易重現該錯誤。  
  
> [!NOTE]
>  `/errorreport` 選項無法在 Visual Studio 開發環境內使用，只有在命令列編譯時才能使用。  
  
## 範例  
 下列程式碼會嘗試編譯 `T2.vb`，如果編譯器發生編譯器內部錯誤，則會提示您將錯誤報告傳送給 Microsoft。  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)