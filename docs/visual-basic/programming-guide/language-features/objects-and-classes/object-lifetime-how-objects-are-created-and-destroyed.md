---
title: 物件存留期：物件的建立和終結
ms.date: 07/20/2015
f1_keywords:
- vb.Constructor
helpviewer_keywords:
- destructors, object lifetime
- Sub Finalize destructor
- objects [Visual Basic], destroying
- lifetime [Visual Basic], objects
- Sub New constructor, object lifetime
- Finalize method [Visual Basic], object lifetime
- objects [Visual Basic], creating
- Class_Terminate
- Dispose method [Visual Basic], object lifetime
- Class_Initialize
- object creation [Visual Basic], object lifetime
- parameterized constructors
- objects [Visual Basic], lifetime
- objects [Visual Basic], garbage collection
- constructors [Visual Basic], object lifetime
- Sub Dispose destructor
- garbage collection [Visual Basic], Visual Basic
ms.assetid: f1ee8458-b156-44e0-9a8a-5dd171648cd8
ms.openlocfilehash: 8d9647fa490077f9f6ef82f30eccc4d5ee271985
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346099"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>物件存留期：物件的建立和終結 (Visual Basic)

您可以使用 `New` 關鍵字來建立類別的執行個體，即物件。 在使用新物件之前，經常必須在新物件上執行初始設定工作。 常見的初始設定工作包括開啟檔案、連線到資料庫，以及讀取登錄機碼的值。 Visual Basic controls the initialization of new objects using procedures called *constructors* (special methods that allow control over initialization).

物件離開範圍之後，它會被通用語言執行平台 (CLR) 所釋放。 Visual Basic controls the release of system resources using procedures called *destructors*. 建構函式與解構函式一起支援建立穩固和可預測的類別庫。

## <a name="using-constructors-and-destructors"></a>使用建構函式和解構函式

建構函式和解構函式控制物件的建立和解構。 The `Sub New` and `Sub Finalize` procedures in Visual Basic initialize and destroy objects; they replace the `Class_Initialize` and `Class_Terminate` methods used in Visual Basic 6.0 and earlier versions.

### <a name="sub-new"></a>Sub New

`Sub New` 建構函式只能在建立類別時執行一次。 不能從相同類別或衍生類別中的其他建構函式的程式碼的第一行以外的任何地方明確呼叫它。 此外，`Sub New` 方法中的程式碼永遠會在類別中的任何其他程式碼執行之前執行。 Visual Basic implicitly creates a `Sub New` constructor at run time if you do not explicitly define a `Sub New` procedure for a class.

若要建立類別的建構函式，請在類別定義中的任何地方建立名為 `Sub New` 的程序。 若要建立參數化建構函式，請指定 `Sub New` 之引數的名稱和資料類型，就像您會為任何其他程序指定引數一樣，如下列程式碼所示：

[!code-vb[VbVbalrOOP#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#42)]

建構函式經常會多載，如下列程式碼所示：

[!code-vb[VbVbalrOOP#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#116)]

當您定義衍生自另一個類別的類別時，建構函式的第一行必須是基底類別建構函式的呼叫，除非基底類別具有不帶任何參數的可存取建構函式。 例如，包含上述建構函式的基底類別呼叫就是 `MyBase.New(s)`。 Otherwise, `MyBase.New` is optional, and the Visual Basic runtime calls it implicitly.

撰寫程式碼以呼叫父物件的建構函式之後，您可以將任何其他初始設定程式碼加入 `Sub New` 程序。 `Sub New` 在被當做參數化建構函式呼叫時，可以接受引數。 會從呼叫建構函式的程序傳遞這些參數，例如，`Dim AnObject As New ThisClass(X)`。

### <a name="sub-finalize"></a>Sub Finalize

釋放物件之前，CLR 會自動針對定義 `Finalize` 程序的物件呼叫 `Sub Finalize` 方法。 `Finalize` 方法可以包含必須在物件被終結之前執行的程式碼，例如關閉檔案和儲存狀態資訊的程式碼。 執行 `Sub Finalize` 對於效能會有些許負面影響，所以您應該只在需要明確釋放物件時才定義 `Sub Finalize` 方法。

> [!NOTE]
> The garbage collector in the CLR does not (and cannot) dispose of *unmanaged objects*, objects that the operating system executes directly, outside the CLR environment. 這是因為必須以不同的方式處置不同的 Unmanaged 物件。 該資訊不是與 Unmanaged 物件直接相關聯；它必須位於物件的文件中。 使用 Unmanaged 物件的類別必須以其 `Finalize` 方法處置它們。

`Finalize` 解構函式是受保護的方法，只能從其所屬的類別或衍生類別呼叫。 系統會在物件被終結時自動呼叫 `Finalize`，所以您不應該從衍生類別的 `Finalize` 實作外明確地呼叫 `Finalize`。

有別於 `Class_Terminate` 會在物件未設定為任何設定時立即執行，物件失去範圍的時間與 Visual Basic 呼叫 `Finalize` 解構函式的時間之間通常會有延遲。 Visual Basic .NET allows for a second kind of destructor, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>, which can be explicitly called at any time to immediately release resources.

> [!NOTE]
> `Finalize` 解構函式不應該擲回例外狀況，因為應用程式無法處理它們，而且可能會導致應用程式終止。

### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>新方法和 Finalize 方法在類別階層中的運作方式

每當建立類別的執行個體時，通用語言執行平台 (CLR) 會嘗試執行名為 `New` 的程序 (如果它存在於該物件)。 `New` 是一種稱為 `constructor` 的程序，用來在物件中的任何其他程式碼執行之前初始化新物件。 `New` 建構函式可以用來開啟檔案、連接到資料庫、初始化變數，以及處理必須先完成才能使用物件的任何其他工作。

建立衍生類別的執行個體時，基底類別的 `Sub New` 的建構函式會最先執行，然後衍生類別中的建構函式接著執行。 這是因為 `Sub New` 建構函式的程式碼中的第一行使用語法 `MyBase.New()` 呼叫在類別階層中在其本身正上方之類別的建構函式。 然後會針對類別階層中的每個類別呼叫 `Sub New` 建構函式，直到達到基底類別的建構函式。 此時，會執行基底類別的建構函式中的程式碼，接著執行所有衍生類別中的每個建構函式中的程式碼，最後執行最多衍生類別中的程式碼。

![Screenshot showing class hierarchy constructors and inheritance.](./media/object-lifetime-how-objects-are-created-and-destroyed/subnew-constructor-inheritance.gif)

當不再需要某物件時，CLR 就會針對該物件呼叫 <xref:System.Object.Finalize%2A> 方法，然後再釋放其記憶體。 <xref:System.Object.Finalize%2A> 方法會呼叫 `destructor`、因為它會執行清理工作 (例如儲存狀態資訊、關閉檔案和連接至資料庫) 以及在釋放物件之前必須完成的其他工作。

![Screenshot showing the Finalize method destructor.](./media/object-lifetime-how-objects-are-created-and-destroyed/finalize-method-destructor.gif)

## <a name="idisposable-interface"></a>IDisposable 介面

類別執行個體經常會控制不受 CLR 管理的資源，例如 Windows 控制代碼和資料庫連線。 這些資源必須在類別的 `Finalize` 方法中處置，這樣在記憶體回收行程終結物件時就會釋放它們。 然而，記憶體回收行程只會在 CLR 需要更多的可用記憶體時才會終結物件。 這表示在物件超出範圍之前可能不會釋放資源。

為了補充記憶體回收，您的類別可以提供機制以主動管理系統資源，不過前提是它們實作 <xref:System.IDisposable> 介面。 <xref:System.IDisposable> 具有 <xref:System.IDisposable.Dispose%2A> 這種方法，當用戶端完成使用物件時，它們應該加以呼叫。 您可以使用 <xref:System.IDisposable.Dispose%2A> 方法立即釋放資源及執行工作，例如關閉檔案和資料庫連線。 與 `Finalize` 解構函式不同的是，不會自動呼叫 <xref:System.IDisposable.Dispose%2A> 方法。 當您想要立即釋放資源時，類別的用戶端必須明確地呼叫 <xref:System.IDisposable.Dispose%2A>。

### <a name="implementing-idisposable"></a>實作 IDisposable

實作 <xref:System.IDisposable> 介面的類別應該包含以下幾段程式碼：

- 追蹤是否已處置物件的欄位：

  ```vb
  Protected disposed As Boolean = False
  ```

- <xref:System.IDisposable.Dispose%2A> 多載，會釋放該類別的資源。 這個方法應該由基底類別的 <xref:System.IDisposable.Dispose%2A> 和 `Finalize` 方法呼叫：

  ```vb
  Protected Overridable Sub Dispose(ByVal disposing As Boolean)
      If Not Me.disposed Then
          If disposing Then
              ' Insert code to free managed resources.
          End If
          ' Insert code to free unmanaged resources.
      End If
      Me.disposed = True
  End Sub
  ```

- 僅包含下列程式碼的 <xref:System.IDisposable.Dispose%2A> 實作：

  ```vb
  Public Sub Dispose() Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
  End Sub
  ```

- 僅包含下列程式碼的 `Finalize` 方法置換：

  ```vb
  Protected Overrides Sub Finalize()
      Dispose(False)
      MyBase.Finalize()
  End Sub
  ```

### <a name="deriving-from-a-class-that-implements-idisposable"></a>從實作 IDisposable 的類別衍生

從實作 <xref:System.IDisposable> 介面之基底類別衍生的類別不需要覆寫任何基底方法，除非它使用需要處置的其他資源。 在該情況下，衍生的類別應該覆寫基底類別的 `Dispose(disposing)` 方法來處置衍生類別的資源。 這個覆寫必須呼叫基底類別的 `Dispose(disposing)` 方法。

```vb
Protected Overrides Sub Dispose(ByVal disposing As Boolean)
    If Not Me.disposed Then
        If disposing Then
            ' Insert code to free managed resources.
        End If
        ' Insert code to free unmanaged resources.
    End If
    MyBase.Dispose(disposing)
End Sub
```

衍生類別不應該覆寫基底類別的 <xref:System.IDisposable.Dispose%2A> 和 `Finalize` 方法。 從衍生類別的執行個體呼叫那些方法時，基底類別對於那些方法的實作會呼叫衍生類別的 `Dispose(disposing)` 方法覆寫。

## <a name="garbage-collection-and-the-finalize-destructor"></a>記憶體回收和 Finalize 解構函式

The .NET Framework uses the *reference-tracing garbage collection* system to periodically release unused resources. Visual Basic 6.0 and earlier versions used a different system called *reference counting* to manage resources. 這兩個系統固然會自動執行相同的功能，不過有幾個重要的差異。

當系統決定不再需要這類物件時，CLR 會定期終結該物件。 當系統資源短缺時，會更快釋放物件，反之則較不常釋放物件。 物件失去範圍的時間與 CLR 釋放它的時間之間的延遲表示，與 Visual Basic 6.0 及舊版中的物件不同的是，您無法精確判斷何時將會終結物件。 In such a situation, objects are said to have *non-deterministic lifetime*. 在大部分的情況下，不具決定性存留期不會變更撰寫應用程式的方式，只要記住，`Finalize` 解構函式可能不會在物件失去範圍時立即執行。

記憶體回收系統之間的另一個差異牽涉到使用 `Nothing`。 若要利用 Visual Basic 6.0 及舊版中的參考計數，程式設計師有時候會將 `Nothing` 指派給物件變數，以釋放那些變數所保留的參考。 如果變數保留物件的最後參考，就會立即釋放物件資源。 在新版 Visual Basic 中，雖然可能在一些情況下，此程序仍相當重要，但是執行它永遠不會造成參考的物件立即釋放其資源。 若要立即釋放資源，請使用物件的 <xref:System.IDisposable.Dispose%2A> 方法 (若有的話)。 唯一應該將變數設定為 `Nothing` 的時間，是在它的存留期相對於記憶體回收行程偵測失去關聯之物件所需的時間較長時。

## <a name="see-also"></a>請參閱

- <xref:System.IDisposable.Dispose%2A>
- [Initialization and Termination of Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))
- [New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)
- [清除 Unmanaged 資源](../../../../standard/garbage-collection/unmanaged.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
