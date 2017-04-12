---
title: "參數和傳回值的多執行緒程序 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d5d8adde531d31aa6bf353f53bd4cfecc084f515
ms.lasthandoff: 03/13/2017

---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>參數和傳回值的多執行緒程序 (Visual Basic)
提供和傳回值的多執行緒應用程式中很複雜，因為執行緒類別的建構函式必須傳遞到採用任何引數，且不傳回值的程序的參考。 下列各節說明一些簡單的方法來提供參數，以及從程序傳回值，在個別執行緒上。  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>如需多執行緒程序中提供的參數  
 提供多執行緒的方法呼叫參數的最佳方式是將目標方法包裝在類別中，並將做為參數的新執行緒的類別定義欄位。 這種方法的優點是，您可以建立類別的新執行個體使用它自己的參數，每次您想要啟動新執行緒。 例如，假設您有函式會計算區域中的三角形，如下列程式碼所示︰  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 您可以撰寫類別包裝`CalcArea`函式並建立欄位來儲存輸入的參數，如下所示︰  
  
```vb  
Class AreaClass  
    Public Base As Double  
    Public Height As Double  
    Public Area As Double  
    Sub CalcArea()  
        Area = 0.5 * Base * Height  
        MessageBox.Show("The area is: " & Area.ToString)  
    End Sub  
End Class  
```  
  
 若要使用`AreaClass`，您可以建立`AreaClass`物件，然後設定`Base`和`Height`屬性，如下列程式碼所示︰  
  
```vb  
Protected Sub TestArea()  
    Dim AreaObject As New AreaClass  
    Dim Thread As New System.Threading.Thread(  
                        AddressOf AreaObject.CalcArea)  
    AreaObject.Base = 30  
    AreaObject.Height = 40  
    Thread.Start()  
End Sub  
```  
  
 請注意，`TestArea`程序不會檢查值`Area`欄位之後呼叫`CalcArea`方法。 因為`CalcArea`個別的執行緒上執行`Area`欄位不保證只有當您呼叫之後立即檢查設定`Thread.Start`。 下一節中討論更好的方法，從多執行緒程序傳回值。  
  
## <a name="returning-values-from-multithreaded-procedures"></a>從多執行緒程序傳回值  
 從個別執行緒執行的程序傳回值複雜的程序不可為函式，且無法使用`ByRef`引數。 傳回值的最簡單方式是使用<xref:System.ComponentModel.BackgroundWorker>元件來管理您的執行緒，並引發事件的工作完成時，並處理與事件處理常式的結果。</xref:System.ComponentModel.BackgroundWorker>  
  
 下列範例會傳回值，藉由引發另一個執行緒上執行的程序中的事件︰  
  
```vb  
Private Class AreaClass2  
    Public Base As Double  
    Public Height As Double  
    Function CalcArea() As Double  
        ' Calculate the area of a triangle.  
        Return 0.5 * Base * Height  
    End Function  
End Class  
  
Private WithEvents BackgroundWorker1 As New System.ComponentModel.BackgroundWorker  
  
Private Sub TestArea2()  
    Dim AreaObject2 As New AreaClass2  
    AreaObject2.Base = 30  
    AreaObject2.Height = 40  
  
    ' Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2)  
End Sub  
  
' This method runs on the background thread when it starts.  
Private Sub BackgroundWorker1_DoWork(  
    ByVal sender As Object,   
    ByVal e As System.ComponentModel.DoWorkEventArgs  
    ) Handles BackgroundWorker1.DoWork  
  
    Dim AreaObject2 As AreaClass2 = CType(e.Argument, AreaClass2)  
    ' Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea()  
End Sub  
  
' This method runs on the main thread when the background thread finishes.  
Private Sub BackgroundWorker1_RunWorkerCompleted(  
    ByVal sender As Object,  
    ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
    ) Handles BackgroundWorker1.RunWorkerCompleted  
  
    ' Access the result through the Result property.  
    Dim Area As Double = CDbl(e.Result)  
    MessageBox.Show("The area is: " & Area.ToString)  
End Sub  
```  
  
 您可以提供參數，並使用選擇性的數值傳回執行緒集區執行緒`ByVal`狀態物件變數<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>方法。</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 執行緒計時器執行緒也支援狀態物件，針對此目的。 如需執行緒集區和執行緒計時器，請參閱[執行緒集區 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[執行緒集區](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701)和[執行緒計時器 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰ 使用 BackgroundWorker 元件 (Visual Basic) 的多執行緒處理](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)   
 [執行緒集區 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)   
 [執行緒同步處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)   
 [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)   
 [多執行緒應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)   
 [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [多執行緒元件](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
