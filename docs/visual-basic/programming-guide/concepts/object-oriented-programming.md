---
title: 物件導向程式設計 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: e8936eb9031ef68ea333835d8433e1ba1a45990f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655963"
---
# <a name="object-oriented-programming-visual-basic"></a>物件導向程式設計 (Visual Basic)
Visual Basic 提供完整的支援包括封裝、 繼承和多型物件導向程式設計。  
  
 「封裝」指的是將一組相關的屬性、方法和其他成員，視為單一單位或物件。  
  
 「繼承」則是描述依據現有類別來建立新類別的能力。  
  
 「多型」指的是您可以有多個交替使用的類別，即使每個類別是以不同的方式來實作相同的屬性或方法。  
  
 本節將說明下列概念：  
  
-   [類別與物件](#classes-and-objects)  
  
    -   [類別成員](#members)  
  
         [屬性和欄位](#properties-and-fields)  
  
         [方法](#methods)  
  
         [建構函式](#constructors)  
  
         [解構函式](#destructors)  
  
         [事件](#events)  
  
         [巢狀的類別](#nested-classes)  
  
    -   [存取修飾詞與存取層級](#access-modifiers-and-access-levels)  
  
    -   [執行個體化類別](#instantiating-classes)  
  
    -   [共用的類別和成員](#shared-classes-and-members)  
  
    -   [匿名型別](#anonymous-types)  
  
-   [繼承](#inheritance)  
  
    -   [覆寫成員](#overriding-members)  
  
-   [介面](#interfaces)  
  
-   [泛型](#generics)  
  
-   [委派](#delegates)  
  
## <a name="classes-and-objects"></a>類別與物件  
「類別」和「物件」有時會交換使用，但事實上，類別說的是物件的「型別」，而物件則是類別之可使用的「執行個體」。 因此，建立物件的動作稱為「具現化」。 再以藍圖作比喻，若類別是藍圖，物件就是根據藍圖所蓋的建築物。

若要定義類別：

```vb  
Class SampleClass
End Class
```

Visual Basic 也提供輕量版的類別，稱為*結構*，可在當您需要建立龐大物件陣列，而且不想要該耗用太多記憶體。

若要定義結構：  

```vb
Structure SampleStructure
End Structure
```

如需詳細資訊，請參閱:

- [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)

- [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a>類別成員
每個類別都有不同的「類別成員」，包括描述類別資料的屬性、定義類別行為的方法，以及提供不同類別與物件之間通訊的事件。

#### <a name="properties-and-fields"></a>屬性和欄位
欄位和屬性表示物件包含的資訊。 欄位就像是變數，可直接讀取或設定。

若要定義欄位：

```vb
Class SampleClass
    Public SampleField As String
End Class
```

屬性具有取得和設定程序，讓您更容易控制設定與傳回數值的方式。

Visual Basic 可讓您可以建立私用欄位來儲存屬性值或使用所謂的自動實作屬性，建立此欄位自動在幕後，並提供屬性程序的基本邏輯。

若要定義自動實作屬性：

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

如果您需要執行某些額外作業來讀取和寫入屬性值，請定義用來儲存屬性值的欄位，並提供儲存和擷取這個欄位的基本邏輯：

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

大部分屬性都具有方法或程序，可以設定及取得屬性值。 但是您可以建立唯讀或唯寫屬性來限制不得修改或讀取。 在 Visual Basic 中，您可以使用 `ReadOnly` 和 `WriteOnly` 關鍵字。 不過，自動實作的屬性不可以是唯讀或唯寫。

如需詳細資訊，請參閱:
  
-   [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)  
  
-   [Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)  
  
-   [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
  
-   [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
  
#### <a name="methods"></a>方法  
 「方法」是物件可執行的動作。  

> [!NOTE]
>  在 Visual Basic 中，有兩個建立方法的方式：如果方法沒有傳回值，即使用 `Sub` 陳述式；如果有傳回值，則使用 `Function` 陳述式。

若要定義類別的方法：

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

類別可以有同一個方法的多個實作或「多載」，但是這些實作的參數個數和參數類型並不相同。

若要多載方法：

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

在多數情況下，您是在類別定義中宣告方法。 不過，Visual Basic 也支援*擴充方法*可讓您將方法加入至現有的類別之類別的實際定義之外。

如需詳細資訊，請參閱:

- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  

- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  

- [多載](../../../visual-basic/language-reference/modifiers/overloads.md)  

- [擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  

#### <a name="constructors"></a>建構函式  
建構函式是類別方法，會在建立指定類型的物件時自動執行。 建構函式通常用來初始化新物件的資料成員， 而且只能在建立類別時執行一次。 此外，建構函式中的程式碼永遠會在類別中的任何其他程式碼執行之前執行。 不過，就和其他任何方法一樣，您可以建立多個建構函式多載。

若要定義類別的建構函式：

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class 
```

如需詳細資訊，請參閱：[物件存留期： 物件的建立和終結](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。

#### <a name="destructors"></a>解構函式
解構函式是用來解構類別的執行個體。 在 .NET Framework 中，記憶體回收行程會自動管理應用程式中 Managed 物件的記憶體配置及釋放。 不過，您可能仍然需要解構函式來清除應用程式建立的任何 Unmanaged 資源。 一個類別只能有一個解構函式。

如需 .NET Framework 中之解構函式和記憶體回收的詳細資訊，請參閱[記憶體回收](../../../standard/garbage-collection/index.md)。

#### <a name="events"></a>事件
事件可讓類別或物件在某些相關的事情發生時，告知其他類別或物件。 傳送 (或引發) 事件的類別稱為「發行者」，而接收 (或處理) 事件的類別則稱為「訂閱者」。 如需事件的詳細資訊以及如何引發和處理事件，請參閱[處理和引發事件](../../../standard/events/index.md)。

- 若要宣告事件時，使用[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。

- 若要引發事件，請使用[RaiseEvent 陳述式](../../../visual-basic/language-reference/statements/raiseevent-statement.md)。

- 若要指定事件處理常式使用以宣告方式，使用[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)陳述式和[處理](../../../visual-basic/language-reference/statements/handles-clause.md)子句。

- 若要能夠以動態方式加入、 移除及變更與事件相關聯的事件處理常式，使用[AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md)和[RemoveHandler 陳述式](../../../visual-basic/language-reference/statements/removehandler-statement.md)搭配[AddressOf運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)。

#### <a name="nested-classes"></a>巢狀的類別  
在類別中定義的另一個類別即稱為「巢狀」類別。 巢狀類別預設為私用。

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

若要建立巢狀類別的執行個體，請使用容器類別名稱，後面加上點號，再接著巢狀類別名稱，如下所示：

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>存取修飾詞與存取層級  
所有類別及類別成員都可以使用「存取修飾詞」，指定要提供給其他類別的存取層級。

下列為可用的存取修飾詞：

|Visual Basic 修飾詞|定義|
|---------------------------|----------------|
|[Public](../../../visual-basic/language-reference/modifiers/public.md)|類型或成員可由相同組件或參考該組件的另一個組件中的任何其他程式碼存取。|
|[Private](../../../visual-basic/language-reference/modifiers/private.md)|類型或成員只能由相同類別中的程式碼存取。|
|[Protected](../../../visual-basic/language-reference/modifiers/protected.md)|類型或成員只能由相同類別中，或是衍生類別中的程式碼存取。|
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|類型或成員可由相同組件中的任何程式碼存取，但是不包括其他組件中的程式碼。|
|`Protected Friend`|類型或成員可由相同組件中的任何程式碼，或是其他組件中的任何衍生類別存取。|

如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。

### <a name="instantiating-classes"></a>執行個體化類別  
若要建立物件，您必須將類別執行個體化，或是建立類別執行個體。

```vb
Dim sampleObject as New SampleClass()
```

將類別執行個體化之後，您就可以將值指派給執行個體的屬性和欄位，並叫用類別方法。

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

若要在類別執行個體化期間將值指派給屬性，請使用物件初始設定式：

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

如需詳細資訊，請參閱:

- [New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)

- [物件初始設定式：具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

###  <a name="Static"></a> 共用的類別和成員  
 共用的類別的成員為屬性、 程序或共用的所有類別執行個體的欄位。  
  
 若要定義共用的成員：  
  
```vb  
Class SampleClass  
    Public Shared SampleString As String = "Sample String"  
End Class  
```  
  
 若要存取共用的成員，請使用類別的名稱而不需要建立此類別的物件：  
  
```vb  
MsgBox(SampleClass.SampleString)  
```  
  
 在 Visual Basic 中的共用的模組有共用僅包含成員，而且無法具現化。 共用的成員也無法存取非共用的屬性、 欄位或方法  
  
 如需詳細資訊，請參閱:  
  
-   [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
  
-   [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)  
  
### <a name="anonymous-types"></a>匿名型別  
使用匿名類型建立物件時，您不需要撰寫資料類型的類別定義， 編譯器 (Compiler) 會自動幫您建立類別 (Class)。 這個類別沒有可使用的名稱，但是包含您在宣告物件時指定的屬性。

若要建立匿名類型的執行個體：

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

如需詳細資訊，請參閱[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。

## <a name="inheritance"></a>繼承
繼承可讓您建立新類別以重複使用、擴充和修改其他類別中定義的行為。 成員被繼承的類別稱為「基底類別」，而繼承這種成員的類別即稱為「衍生類別」。 不過，在 Visual Basic 中的所有類別隱含都繼承自<xref:System.Object>類別支援.NET 類別階層架構，並提供所有類別的低階服務。

> [!NOTE]
>  Visual Basic 不支援多重繼承。 也就是說，您只能為衍生類別指定一個基底類別。

若要繼承基底類別：

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

所有類別預設都可以被繼承。 不過，您可以指定類別是否不得當做基底類別，或是建立只能當做基底類別的類別。

若要指定類別不得當做基底類別使用：

```vb
NotInheritable Class SampleClass
End Class
```

若要指定類別只能當做基底類別且無法執行個體化：

```vb
MustInherit Class BaseClass
End Class
```

如需詳細資訊，請參閱:

- [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)

- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>覆寫成員
衍生類別預設會從其基底類別繼承所有成員。 如果想要變更所繼承成員的行為，您必須覆寫這個成員。 也就是說，您可以定義衍生類別中方法、屬性或事件的新實作。

下列修飾詞是用來控制如何覆寫屬性及方法：

|Visual Basic 修飾詞|定義|
|---------------------------|----------------|
|[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)|允許在衍生類別中覆寫類別成員。|
|[Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)|覆寫在基底類別中定義的虛擬 (可覆寫) 成員。|
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|防止在繼承的類別中覆寫成員。|
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|要求在衍生類別中覆寫類別成員。|
|[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)|隱藏繼承自基底類別的成員。|

## <a name="interfaces"></a>介面
介面就像類別，可定義屬性、方法和事件集。 但與類別不同的是，介面並不提供實作。 介面是由類別實作，並定義為與類別不同的實體。 介面就代表著一種合約，因為實作介面的類別必須完全依介面的定義來實作這個介面的各個方面。

若要定義介面：

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

若要在類別中實作介面：

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

如需詳細資訊，請參閱:

- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  

- [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  

- [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)  

## <a name="generics"></a>泛型
類別、 結構、 介面和方法在.NET 中的可以包含*型別參數*可定義類型的物件，而且可以儲存或使用。 泛型最常見的範例是集合，您可以在其中指定要儲存於集合之物件的類型。  

若要定義泛型類別：

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

若要建立泛型類別的執行個體：

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

如需詳細資訊，請參閱:

- [泛型](~/docs/standard/generics/index.md)

- [Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a>委派
 「委派」是定義方法簽章的類型，可以提供任何具有相容簽章之方法的參考。 您可以透過委派叫用 (Invoke) 或呼叫方法。 委派可以用來將方法當做引數傳遞給其他方法。

> [!NOTE]
>  事件處理常式就是透過委派叫用的方法。 如需使用委派處理事件的詳細資訊，請參閱[處理和引發事件](../../../standard/events/index.md)。

若要建立委派：

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

若要建立與委派所指定簽章相符之方法的參考：

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

如需詳細資訊，請參閱:

- [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)

- [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>另請參閱
 [Visual Basic 程式設計手冊](../../../visual-basic/programming-guide/index.md)
