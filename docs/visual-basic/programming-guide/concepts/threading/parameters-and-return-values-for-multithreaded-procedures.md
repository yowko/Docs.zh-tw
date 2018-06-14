---
title: 參數和傳回值的多執行緒程序 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
ms.openlocfilehash: 039e9be6f174148995a83c842a442806b9409a3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648095"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>參數和傳回值的多執行緒程序 (Visual Basic)
在多執行緒應用程式中提供和傳回值很複雜，因為執行緒類別的建構函式必須傳遞到不採用任何引數且不傳回任何值的程序參考。 下節會說明一些簡單的方法來提供參數，以及從不同執行緒的程序傳回值。  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>為多執行緒程序提供參數  
 為多執行緒方法呼叫提供參數的最佳方式，是將目標方法包裝在類別中，並為要用為新執行緒參數的類別定義欄位。 這種方法的優點是您可以建立類別的新執行個體，每次想要開始新執行緒都可以使用它自己的參數。 例如，假設您有計算三角形面積的函式，如下列程式碼所示︰  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 您可以撰寫類別，包裝 `CalcArea` 函式並建立儲存輸入參數的欄位，如下所示︰  
  
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
  
 若要使用 `AreaClass`，您可以建立 `AreaClass` 物件，然後設定 `Base` 和 `Height` 屬性，如下列程式碼所示︰  
  
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
  
 請注意，呼叫 `CalcArea` 方法之後，`TestArea` 程序不會檢查 `Area` 欄位的值。 如果您在呼叫 `Thread.Start` 之後立即檢查，因為 `CalcArea` 在另外的執行緒上執行，所以不保證會設定 `Area` 欄位。 下節會討論從多執行緒程序傳回值的更好方法。  
  
## <a name="returning-values-from-multithreaded-procedures"></a>從多執行緒程序傳回值  
 從在其他執行緒上執行的程序傳回值很複雜，因為這些程序不能是函式，也無法使用 `ByRef` 引數。 傳回值最簡單的方式是使用 <xref:System.ComponentModel.BackgroundWorker> 元件來管理您的執行緒，並在工作完成時引發事件，然後以事件處理常式來處理結果。  
  
 下例會透過從在另一個執行緒上執行的程序引發事件傳回值：  
  
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
  
 您可以使用 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 方法的選擇性 `ByVal` 狀態物件變數，提供參數並將值傳回給執行緒集區執行緒。 執行緒計時器執行緒也支援針對此目的狀態物件。 在執行緒集區和執行緒計時器上的資訊，請參閱[執行緒集區 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[執行緒集區](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701)和[執行緒計時器 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：使用 BackgroundWorker 元件進行多執行緒處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [執行緒集區 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [執行緒同步處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [多執行緒應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [元件中的多執行緒](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
