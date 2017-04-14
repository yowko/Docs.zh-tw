---
title: "如何：執行物件的延遲初始化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET 中的延遲初始設定, 如何執行"
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：執行物件的延遲初始化
<xref:System.Lazy%601?displayProperty=fullName> 類別使得將物件延遲初始化和延遲執行個體化的工作變得簡單。  藉由將物件延遲初始化，您不必再事先建立可能永遠都用不到的物件，而且可以將物件延到初次存取該物件時再初始化。  如需詳細資訊，請參閱[延遲初始設定](../../../docs/framework/performance/lazy-initialization.md)。  
  
## 範例  
 下列範例示範如何使用 <xref:System.Lazy%601> 來初始化一個值。  假設依據將 `someCondition` 變數設為 true 或 false 的其他某個程式碼而定，可能不需要延遲變數。  
  
```vb  
Dim someCondition As Boolean = False  
  
Sub Main()  
    'Initializing a value with a big computation, computed in parallel  
    Dim _data As Lazy(Of Integer) = New Lazy(Of Integer)(Function()  
                                                             Dim result =  
                                                                 ParallelEnumerable.Range(0, 1000).  
                                                                 Aggregate(Function(x, y)  
                                                                               Return x + y  
                                                                           End Function)  
                                                             Return result  
                                                         End Function)  
  
    '  do work that may or may not set someCondition to True  
    ' ...  
    '  Initialize the data only if needed  
    If someCondition = True Then  
  
        If (_data.Value > 100) Then  
  
            Console.WriteLine("Good data")  
        End If  
    End If  
End Sub  
```  
  
```csharp  
  static bool someCondition = false;    
  //Initializing a value with a big computation, computed in parallel  
  Lazy<int> _data = new Lazy<int>(delegate  
  {  
      return ParallelEnumerable.Range(0, 1000).  
          Select(i => Compute(i)).Aggregate((x,y) => x + y);  
  }, LazyExecutionMode.EnsureSingleThreadSafeExecution);  
  
  // Do some work that may or may not set someCondition to true.  
  //  ...  
  // Initialize the data only if necessary  
  if (someCondition)  
{  
    if (_data.Value > 100)  
      {  
          Console.WriteLine("Good data");  
      }  
}  
```  
  
## 範例  
 下列範例示範如何使用 <xref:System.Threading.ThreadLocal%601?displayProperty=fullName> 類別，初始化只有目前執行緒上的目前物件執行個體可見的型別。  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## 請參閱  
 <xref:System.Threading.LazyInitializer?displayProperty=fullName>   
 [延遲初始設定](../../../docs/framework/performance/lazy-initialization.md)