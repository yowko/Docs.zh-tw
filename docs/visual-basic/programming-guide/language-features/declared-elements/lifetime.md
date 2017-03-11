---
title: "Lifetime in Visual Basic | Microsoft Docs"
ms.custom: ""
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
  - "static variables, lifetime"
  - "static variables, Visual Basic"
  - "declared elements, lifetime"
  - "Shared variable lifetime"
  - "lifetime, declared elements"
  - "lifetime, Visual Basic"
  - "lifetime"
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Lifetime in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

宣告項目的「*存留期*」\(Lifetime\) 是指可以使用該項目的一段時間。  變數是唯一擁有存留期的項目。  因此，編譯器會將程序參數和函式傳回的內容視為是變數的特殊案例。  變數的存留期代表它可保留一個值的期間。  過了變數的存留期後，它的值可能會改變，但它永遠會保留某個值。  
  
## 不同的存留期  
 「*成員變數*」\(Member Variable\) \(在任何程序以外宣告的模組層級變數\) 的存留期通常會與宣告該變數的項目相同。  在類別或結構中宣告的非共用變數，是供宣告該變數的類別或結構執行個體 \(Instance\) 所使用。  這類的變數的存留期與其執行個體相同。  但是，`Shared` 變數只有一個存留期，可在應用程式執行的整個期間延續。  
  
 「*區域變數*」\(Local Variable\) \(在程序內宣告的變數\) 只有在宣告該變數的程序執行時才存在。  該程序的參數與任何函式傳回的內容也是如此。  但是，如果該程序呼叫其他程序，區域變數在受呼叫程序執行時將保留它們的值。  
  
## 存留期的開始  
 當控制權進入宣告區域變數的程序時，區域變數的存留期即開始。  只要程序一開始執行，每個區域變數就會初始化為所屬資料型別的預設值。  當程序進行到指定初始值的 `Dim` 陳述式 \(Statement\) 時，會將這些變數設定為初始值，即使程式碼已指派了其他值也一樣。  
  
 結構變數中的每一個成員都會被視為個別的變數加以初始化。  同樣地，陣列變數中的每一個項目也都會分別被初始化。  
  
 在程序內區塊 \(例如 `For` 迴圈\) 中宣告的變數，在進入程序時會進行初始化。  無論您的程式碼是否執行該區塊，都會執行初始化。  
  
## 存留期的結束  
 當程序結束時，不會保留其區域變數的值，而且 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會回收這些變數使用的記憶體。  當您下次呼叫此程序時，會從頭開始建立所有區域變數並將之重新初始化。  
  
 當類別或結構的執行個體結束時，非共用變數就會從記憶體移除並失去值。  每次建立類別或結構的新執行個體時，會建立非共用變數並將之重新初始化。  不過，`Shared` 變數會保存至應用程式停止執行為止。  
  
## 存留期的擴充  
 如果您使用 `Static` 關鍵字宣告區域變數，該變數的存留期會比程序的執行時間來得長。  下表顯示程序宣告如何判斷 `Static` 變數的存在時間。  
  
|程序位置及共用與否|靜態變數存留期開始|靜態變數存留期結束|  
|---------------|---------------|---------------|  
|在模組中 \(依預設共用\)|第一次呼叫程序時|當應用程式停止執行時|  
|在類別中，`Shared` \(程序不是執行個體成員\)|第一次以特定執行個體或以類別或結構的名稱呼叫程序時|當應用程式停止執行時|  
|在類別的執行個體中，非 `Shared` \(程序是執行個體成員\)|第一次以特定執行個體呼叫程序時|當執行個體釋出以進行記憶體回收 \(GC\) 時|  
  
## 相同名稱的靜態變數  
 您可以在多個程序中以相同的名稱宣告靜態變數。  如果這麼做，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會將此類變數視為個別項目。  其中一個變數的初始化並不會影響其他變數的值。  如果您要以一組多載來定義程序，並在每一個多載中以相同的名稱來宣告靜態變數，也可以套用這個方法。  
  
## 靜態變數的包含項目  
 您可以在類別中宣告靜態區域變數，也就是在該類別的程序中宣告。  但是您無法在結構中宣告靜態區域變數，不論是該結構中的結構成員，還是結構內程序中的區域變數，都無法宣告。  
  
## 範例  
  
### 描述  
 下列範例是使用 [Static](../../../../visual-basic/language-reference/modifiers/static.md) 關鍵字的變數宣告。  \(請注意，當 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 使用如 `Static` 的修飾詞時，不需使用 `Dim` 關鍵字\)。  
  
### 程式碼  
 [!code-vb[VbVbalrKeywords#13](../../../../visual-basic/language-reference/codesnippet/visualbasic/lifetime_1.vb)]  
  
### 註解  
 在前述範例中，在程序 `runningTotal` 傳回呼叫程式碼後，變數 `applesSold` 仍會繼續存在。  下次呼叫 `runningTotal` 時，`applesSold` 會保留之前的計算值。  
  
 如果未使用 `Static` 宣告 `applesSold`，之前累積的值將不會跨 `runningTotal` 的呼叫而保留下來。  下次呼叫 `runningTotal` 時，將重新建立 `applesSold` 並將其初始值設為 0，而且 `runningTotal` 只會傳回與這次呼叫相同的值。  
  
### 編譯程式碼  
 您可以初始化靜態區域變數的值，當做宣告的一部分。  如果您將陣列宣告為 `Static`，您可以初始化其陣序規範 \(維度的數目\)、每一個維度的長度和個別項目的值。  
  
### 安全性  
 在前述範例中，您可以在模組層級中宣告 `applesSold` 以產生相同的存留期。  但是如果您以這種方式變更變數範圍，程序就不能再獨佔該變數的存取權。  因為其他程序也可存取 `applesSold` 並變更其值，累加值會可能會無法預期，而且程式碼會更難維護。  
  
## 請參閱  
 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)   
 [Nothing](../../../../visual-basic/language-reference/nothing.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)