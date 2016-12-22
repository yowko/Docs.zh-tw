---
title: "如何：在 LINQ 之外使用 Lambda 運算式 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Lambda 運算式 [C#], LINQ 外面"
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：在 LINQ 之外使用 Lambda 運算式 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Lambda 運算式並不限於 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 查詢。  在預期會使用委派 \(Delegate\) 的任何位置，也就是任何可以使用匿名方法的位置，都可以使用這種運算式。  下列範例會示範如何在 Windows Form 事件處理常式中使用 Lambda 運算式。  請注意，輸入的型別 \(<xref:System.Object> 和 <xref:System.Windows.Forms.MouseEventArgs>\) 是由編譯器 \(Compiler\) 推斷，因此不需要在 Lambda 輸入參數中明確提供。  
  
## 範例  
  
```  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## 請參閱  
 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)