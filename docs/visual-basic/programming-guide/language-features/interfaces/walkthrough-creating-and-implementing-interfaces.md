---
title: "Walkthrough: Creating and Implementing Interfaces (Visual Basic) | Microsoft Docs"
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
  - "interfaces, walkthroughs"
  - "interfaces, testing"
  - "interface implementation, walkthrough"
  - "interfaces, creating"
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Creating and Implementing Interfaces (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

介面描述屬性、方法和事件的特性，但根據結構或類別保留實作細節。  
  
 這個逐步解說示範如何宣告和實作介面。  
  
> [!NOTE]
>  這個逐步解說中並未提供有關如何建立使用者介面的資訊。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### 若要定義介面  
  
1.  開啟新的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows 應用程式專案。  
  
2.  按一下 \[**專案**\] 功能表上的 \[**加入模組**\]，將新模組加入專案中。  
  
3.  將新模組命名為 `Module1.vb` 並按一下 \[**加入**\]。  接著會顯示新模組的程式碼。  
  
4.  在 `Module` 與 `End Module` 陳述式之間輸入 `Interface TestInterface`，並按 ENTER，以在 `Module1` 中定義名為 `TestInterface` 的介面。  \[**程式碼編輯器**\] 會縮排 `Interface` 關鍵字，並加入 `End Interface` 陳述式來形成程式碼區塊。  
  
5.  在 `Interface` 與 `End Interface` 陳述式之間放入下列程式碼以分別定義一個屬性、方法和事件：  
  
     [!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## 實作  
 您可能會注意到用於宣告介面成員的語法與用於宣告類別成員的語法不同。  這樣的差異反映出介面無法包含實作程式碼的事實。  
  
#### 若要實作介面  
  
1.  藉由將下列陳述式加入到 `Module1` 中 `End Interface` 陳述式之後，`End Module` 陳述式之前，再按 ENTER，來新增名為 `ImplementationClass` 的類別：  
  
     [!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     如果您在整合式開發環境中作業，當您按 ENTER 時，\[**程式碼編輯器**\] 會提供相符的 `End Class` 陳述式。  
  
2.  將下列 `Implements` 陳述式加到 `ImplementationClass`，以便命名類別實作的介面：  
  
     [!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     當 `Implements` 陳述式與其他項目分隔並列於類別或結構最上方時，這個陳述式就會指示類別或結構實作介面。  
  
     若是在整合開發環境中工作，則當您按 ENTER 時，\[**程式碼編輯器**\] 將實作 `TestInterface` 所需的類別成員，您可以略過下一步。  
  
3.  若不是在整合開發環境中工作，則必須實作介面 `MyInterface` 的所有成員。  將下列程式碼加到 `ImplementationClass` 以實作 `Event1`、`Method1` 和 `Prop1`：  
  
     [!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     正在實作的介面和介面成員的 `Implements` 陳述式名稱。  
  
4.  將私用欄位加入至儲存屬性值的類別中，以完成 `Prop1` 的定義：  
  
     [!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     從屬性 get 存取子傳回 `pval` 的值。  
  
     [!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     在屬性 set 存取子中設定 `pval` 的值。  
  
     [!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  加入下列程式碼以完成 `Method1` 的定義。  
  
     [!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### 若要測試介面的實作  
  
1.  在 \[**方案總管**\] 中的專案啟動表單上按一下滑鼠右鍵，再按一下 \[**檢視程式碼**\]。  接著編輯器會顯示啟動表單的類別。  根據預設，啟動表單稱為 `Form1`。  
  
2.  將以下 `testInstance` 欄位加入 `Form1` 類別：  
  
     [!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     藉由將 `testInstance` 宣告為 `WithEvents`，`Form1` 類別可處理其事件。  
  
3.  將下列事件處理常式加入 `Form1` 類別，以便處理由 `testInstance` 引發的事件：  
  
     [!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  將名為 `Test` 的副程式加到 `Form1` 類別來測試實作類別：  
  
     [!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     `Test` 程序可建立實作 `MyInterface` 之類別的執行個體，將執行個體指派給 `testInstance` 欄位，設定屬性，再透過介面執行方法。  
  
5.  加入程式碼來從啟動表單的 `Form1 Load` 程序呼叫 `Test` 程序：  
  
     [!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  按 F5 執行 `Test` 程序。  接著會顯示「Prop1 設定為 9」的訊息。  在按一下 \[確定\] 後，會顯示「Method1 的 X 參數為 5」的訊息。  按一下 \[確定\] 隨即會顯示「事件處理常式攔截了該事件」的訊息。  
  
## 請參閱  
 [Implements Statement](../../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)   
 [Interface Statement](../../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md)