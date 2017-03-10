---
title: "Me, My, MyBase, and MyClass in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "MyClass"
  - "vb.Me"
  - "MyBase"
  - "vb.MyBase"
  - "Me"
  - "vb.MyClass"
  - "vb.This"
  - "vb.My"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My object"
  - "self-reference, Me keyword"
  - "MyClass keyword, relationship to similar programming elements"
  - "Me keyword, relationship to similar programming elements"
  - "Me keyword, referring to the current instance of an object"
  - "Me keyword"
  - "self-reference"
  - "current instance, Me keyword"
  - "MyBase keyword, relationship to similar programming elements"
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Me, My, MyBase, and MyClass in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的 `Me`、`My`、`MyBase` 和 `MyClass` 名稱相似，但用途不同。  本主題會說明這當中每個實體之間的差異。  
  
## Me  
 `Me` 關鍵字提供方法，參考目前程式碼正在其中執行之特定類別執行個體或結構。  `Me` 的行為不是和物件變數相同，就是和參考目前執行個體的結構變數相同。  在將關於目前執行中的類別或結構執行個體的資訊傳給其他類別、結構或模組的程序時，`Me` 特別好用。  
  
 例如，假設您的模組中擁有下列程序。  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 使用下列陳述式，您就可以呼叫這個程序，並將 <xref:System.Windows.Forms.Form> 類別目前的執行個體視為引數來傳遞。  
  
```  
ChangeFormColor(Me)  
```  
  
## My  
 `My` 功能提供簡單而直覺的存取方式，可以讓 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 使用者存取各種 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 類別，並與電腦、應用程式、設定、資源等互動。  
  
## MyBase  
 `MyBase` 關鍵字的行為就像參考類別目前執行個體之基底類別的物件變數。  `MyBase` 通常用於存取衍生類別中所覆寫或遮蔽的基底類別成員。  `MyBase.New` 可用於從衍生類別建構函式明確地呼叫基底類別建構函式。  
  
## MyClass  
 `MyClass` 關鍵字的行為就像參考原先實作之類別目前執行個體的物件變數。  `MyClass` 類似於 `Me`，但在處理其上所有方法呼叫時，會將方法視為 `NotOverridable`。  
  
## 請參閱  
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)