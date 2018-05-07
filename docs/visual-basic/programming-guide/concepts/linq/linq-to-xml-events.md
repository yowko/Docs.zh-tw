---
title: LINQ to XML 事件 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: 216c2af87d2ae3a767548ccaa1efe118215cc6a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-xml-events-visual-basic"></a>LINQ to XML 事件 (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 事件可讓您在 XML 樹狀結構有所更改時收到通知。  
  
 您可以將事件加入到任何 <xref:System.Xml.Linq.XObject> 的執行個體。 接著，事件處理常式將會收到修改該 <xref:System.Xml.Linq.XObject> 及其任何子代的事件。 例如，您可以將事件處理常式加入到樹狀結構的根目錄，並從該事件處理常式處理樹狀結構的所有修改。  
  
 如需 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 事件的範例，請參閱 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed>。  
  
## <a name="types-and-events"></a>型別與事件  
 使用事件時，您可以使用下列型別：  
  
|類型|描述|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|引發 <xref:System.Xml.Linq.XObject> 的事件時，指定事件型別。|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|提供 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件的資料。|  
  
 修改 XML 樹狀結構時，會引發下列事件：  
  
|事件|描述|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|只會在此 <xref:System.Xml.Linq.XObject> 或其任何子代即將變更前發生。|  
|<xref:System.Xml.Linq.XObject.Changed>|<xref:System.Xml.Linq.XObject> 已變更時或其任何子代已變更時發生。|  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 當您想要維護 XML 樹狀結構中的特定彙總資訊時，這些事件相當實用。 例如，您可能想要維護發票明細項目總計的發票總數。 此範例使用事件維護複雜項目 `Items` 下，所有子項目的總計。  
  
### <a name="code"></a>程式碼  
  
```vb  
Module Module1  
    Dim WithEvents items As XElement = Nothing  
    Dim total As XElement = Nothing  
    Dim root As XElement = _  
            <Root>  
                <Total>0</Total>  
                <Items></Items>  
            </Root>  
  
    Private Sub XObjectChanged( _  
            ByVal sender As Object, _  
            ByVal cea As XObjectChangeEventArgs) _  
            Handles items.Changed  
        Select Case cea.ObjectChange  
            Case XObjectChange.Add  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
            Case XObjectChange.Remove  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
        End Select  
        Console.WriteLine("Changed {0} {1}", _  
                            sender.GetType().ToString(), _  
                            cea.ObjectChange.ToString())  
    End Sub  
  
    Sub Main()  
        total = root.<Total>(0)  
        items = root.<Items>(0)  
        items.SetElementValue("Item1", 25)  
        items.SetElementValue("Item2", 50)  
        items.SetElementValue("Item2", 75)  
        items.SetElementValue("Item3", 133)  
        items.SetElementValue("Item1", Nothing)  
        items.SetElementValue("Item4", 100)  
        Console.WriteLine("Total:{0}", CInt(total))  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>註解  
 此程式碼會產生下列輸出：  
  
```  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## <a name="see-also"></a>另請參閱  
 [進階的 LINQ to XML 程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
