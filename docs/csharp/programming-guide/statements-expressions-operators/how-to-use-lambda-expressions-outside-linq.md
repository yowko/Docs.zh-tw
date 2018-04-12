---
title: 如何：在 LINQ 之外使用 Lambda 運算式 (C# 程式設計手冊)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c99f6bc7c9db1f0e2341c31ec5bf60217723d4e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>如何：在 LINQ 之外使用 Lambda 運算式 (C# 程式設計手冊)
Lambda 運算式並不限於 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢。 在預期會使用委派的任何位置，也就是任何可以使用匿名方法的位置，都可以使用這種運算式。 下列範例示範如何在 Windows Forms 事件處理常式中使用 Lambda 運算式。 請注意，輸入的類型 (<xref:System.Object> 和 <xref:System.Windows.Forms.MouseEventArgs>) 是由編譯器推斷，因此不需要在 Lambda 輸入參數中明確提供。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
