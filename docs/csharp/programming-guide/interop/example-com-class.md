---
title: "範例 COM 類別 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "COM, 將 Visual C# 物件公開給"
  - "範例 [C#], COM 類別"
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 範例 COM 類別 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

下列是一個類別範例，您會將這個類別公開為 COM 物件。  將程式碼放入 .cs 檔並加入專案後，請將 \[**註冊 COM Interop**\] 屬性設定為 \[**True**\]。  如需詳細資訊，請參閱 [NIB: How to: Register a Component for COM Interop](http://msdn.microsoft.com/zh-tw/4de7d474-56e8-4027-994d-d47ca4725c5e)。  
  
 將 Visual C\# 物件公開為 COM 需要宣告一個類別介面、事件介面 \(如果必要時\) 和類別本身。  類別成員必須遵循以下規則，才可見於 COM：  
  
-   類別必須是公用的  
  
-   屬性、方法和事件必須是公用的  
  
-   屬性和方法必須宣告於類別介面  
  
-   事件必須在事件介面內宣告過  
  
 類別中其他未在此介面內宣告的公用成員將不可見於 COM，但可見於其他 .Net Framework 物件。  
  
 若要將屬性和方法公開給 COM，您必須將它們宣告在類別介面上、使用一個 `DispId` 屬性將它們標記起來，並且在類別中予以實作。  介面中宣告成員的順序即是 COM vtable 所使用的順序。  
  
 若要由您的類別公開事件，必須將它們宣告在事件介面上，並且使用一個 `DispId` 屬性將它們標記起來。  這個類別不可用來實作事件介面。  
  
 這個類別可以實作類別介面，它可以實作一個以上的介面，但是第一個實作的介面將做為預設的類別介面。  請在此實作要公開給 COM 的方法和屬性。  它們必須標記為公用並且符合類別介面內的宣告。  也請在此宣告由類別所引發的事件。  它們必須標記為公用並且符合事件介面內的宣告。  
  
## 範例  
 [!code-cs[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [互通性](../../../csharp/programming-guide/interop/interoperability.md)   
 [專案設計工具、建置頁 \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp)