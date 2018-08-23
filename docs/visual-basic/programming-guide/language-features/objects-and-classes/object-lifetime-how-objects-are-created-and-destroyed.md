---
title: 物件存留期：物件的建立和終結 (Visual Basic)
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
ms.openlocfilehash: 441fe91c8c884e59c6399d57e7e55bf6591cb1bb
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "42754087"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a><span data-ttu-id="18224-102">物件存留期：物件的建立和終結 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18224-102">Object Lifetime: How Objects Are Created and Destroyed (Visual Basic)</span></span>
<span data-ttu-id="18224-103">您可以使用 `New` 關鍵字來建立類別的執行個體，即物件。</span><span class="sxs-lookup"><span data-stu-id="18224-103">An instance of a class, an object, is created by using the `New` keyword.</span></span> <span data-ttu-id="18224-104">在使用新物件之前，經常必須在新物件上執行初始設定工作。</span><span class="sxs-lookup"><span data-stu-id="18224-104">Initialization tasks often must be performed on new objects before they are used.</span></span> <span data-ttu-id="18224-105">常見的初始設定工作包括開啟檔案、連線到資料庫，以及讀取登錄機碼的值。</span><span class="sxs-lookup"><span data-stu-id="18224-105">Common initialization tasks include opening files, connecting to databases, and reading values of registry keys.</span></span> <span data-ttu-id="18224-106">Visual Basic 控制項的使用程序呼叫的新物件初始化*建構函式*（允許控制初始化的特殊方法）。</span><span class="sxs-lookup"><span data-stu-id="18224-106">Visual Basic controls the initialization of new objects using procedures called *constructors* (special methods that allow control over initialization).</span></span>  
  
 <span data-ttu-id="18224-107">物件離開範圍之後，它會被通用語言執行平台 (CLR) 所釋放。</span><span class="sxs-lookup"><span data-stu-id="18224-107">After an object leaves scope, it is released by the common language runtime (CLR).</span></span> <span data-ttu-id="18224-108">Visual Basic 會控制使用呼叫的程序的系統資源的釋放*解構函式*。</span><span class="sxs-lookup"><span data-stu-id="18224-108">Visual Basic controls the release of system resources using procedures called *destructors*.</span></span> <span data-ttu-id="18224-109">建構函式與解構函式一起支援建立穩固和可預測的類別庫。</span><span class="sxs-lookup"><span data-stu-id="18224-109">Together, constructors and destructors support the creation of robust and predictable class libraries.</span></span>  
  
## <a name="using-constructors-and-destructors"></a><span data-ttu-id="18224-110">使用建構函式和解構函式</span><span class="sxs-lookup"><span data-stu-id="18224-110">Using Constructors and Destructors</span></span>  
 <span data-ttu-id="18224-111">建構函式和解構函式控制物件的建立和解構。</span><span class="sxs-lookup"><span data-stu-id="18224-111">Constructors and destructors control the creation and destruction of objects.</span></span> <span data-ttu-id="18224-112">`Sub New`並`Sub Finalize`Visual Basic 中的程序初始化，並終結物件; 它們取代`Class_Initialize`和`Class_Terminate`Visual Basic 6.0 和更早版本中使用的方法。</span><span class="sxs-lookup"><span data-stu-id="18224-112">The `Sub New` and `Sub Finalize` procedures in Visual Basic initialize and destroy objects; they replace the `Class_Initialize` and `Class_Terminate` methods used in Visual Basic 6.0 and earlier versions.</span></span>  
  
### <a name="sub-new"></a><span data-ttu-id="18224-113">Sub New</span><span class="sxs-lookup"><span data-stu-id="18224-113">Sub New</span></span>  
 <span data-ttu-id="18224-114">`Sub New` 建構函式只能在建立類別時執行一次。</span><span class="sxs-lookup"><span data-stu-id="18224-114">The `Sub New` constructor can run only once when a class is created.</span></span> <span data-ttu-id="18224-115">不能從相同類別或衍生類別中的其他建構函式的程式碼的第一行以外的任何地方明確呼叫它。</span><span class="sxs-lookup"><span data-stu-id="18224-115">It cannot be called explicitly anywhere other than in the first line of code of another constructor from either the same class or from a derived class.</span></span> <span data-ttu-id="18224-116">此外，`Sub New` 方法中的程式碼永遠會在類別中的任何其他程式碼執行之前執行。</span><span class="sxs-lookup"><span data-stu-id="18224-116">Furthermore, the code in the `Sub New` method always runs before any other code in a class.</span></span> [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]<span data-ttu-id="18224-117"> 和更新版本會隱含地建立`Sub New`建構函式在執行階段，如果您未明確定義`Sub New`類別的程序。</span><span class="sxs-lookup"><span data-stu-id="18224-117"> and later versions implicitly create a `Sub New` constructor at run time if you do not explicitly define a `Sub New` procedure for a class.</span></span>  
  
 <span data-ttu-id="18224-118">若要建立類別的建構函式，請在類別定義中的任何地方建立名為 `Sub New` 的程序。</span><span class="sxs-lookup"><span data-stu-id="18224-118">To create a constructor for a class, create a procedure named `Sub New` anywhere in the class definition.</span></span> <span data-ttu-id="18224-119">若要建立參數化建構函式，請指定 `Sub New` 之引數的名稱和資料類型，就像您會為任何其他程序指定引數一樣，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="18224-119">To create a parameterized constructor, specify the names and data types of arguments to `Sub New` just as you would specify arguments for any other procedure, as in the following code:</span></span>  
  
 [!code-vb[VbVbalrOOP#42](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_1.vb)]  
  
 <span data-ttu-id="18224-120">建構函式經常會多載，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="18224-120">Constructors are frequently overloaded, as in the following code:</span></span>  
  
 [!code-vb[VbVbalrOOP#116](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_2.vb)]  
  
 <span data-ttu-id="18224-121">當您定義衍生自另一個類別的類別時，建構函式的第一行必須是基底類別建構函式的呼叫，除非基底類別具有不帶任何參數的可存取建構函式。</span><span class="sxs-lookup"><span data-stu-id="18224-121">When you define a class derived from another class, the first line of a constructor must be a call to the constructor of the base class, unless the base class has an accessible constructor that takes no parameters.</span></span> <span data-ttu-id="18224-122">例如，包含上述建構函式的基底類別呼叫就是 `MyBase.New(s)`。</span><span class="sxs-lookup"><span data-stu-id="18224-122">A call to the base class that contains the above constructor, for example, would be `MyBase.New(s)`.</span></span> <span data-ttu-id="18224-123">否則，`MyBase.New`是選擇性的與 Visual Basic 執行階段會隱含呼叫它。</span><span class="sxs-lookup"><span data-stu-id="18224-123">Otherwise, `MyBase.New` is optional, and the Visual Basic runtime calls it implicitly.</span></span>  
  
 <span data-ttu-id="18224-124">撰寫程式碼以呼叫父物件的建構函式之後，您可以將任何其他初始設定程式碼加入 `Sub New` 程序。</span><span class="sxs-lookup"><span data-stu-id="18224-124">After you write the code to call the parent object's constructor, you can add any additional initialization code to the `Sub New` procedure.</span></span> <span data-ttu-id="18224-125">`Sub New` 在被當做參數化建構函式呼叫時，可以接受引數。</span><span class="sxs-lookup"><span data-stu-id="18224-125">`Sub New` can accept arguments when called as a parameterized constructor.</span></span> <span data-ttu-id="18224-126">會從呼叫建構函式的程序傳遞這些參數，例如，`Dim AnObject As New ThisClass(X)`。</span><span class="sxs-lookup"><span data-stu-id="18224-126">These parameters are passed from the procedure calling the constructor, for example, `Dim AnObject As New ThisClass(X)`.</span></span>  
  
### <a name="sub-finalize"></a><span data-ttu-id="18224-127">Sub Finalize</span><span class="sxs-lookup"><span data-stu-id="18224-127">Sub Finalize</span></span>  
 <span data-ttu-id="18224-128">釋放物件之前，CLR 會自動針對定義 `Finalize` 程序的物件呼叫 `Sub Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="18224-128">Before releasing objects, the CLR automatically calls the `Finalize` method for objects that define a `Sub Finalize` procedure.</span></span> <span data-ttu-id="18224-129">`Finalize` 方法可以包含必須在物件被終結之前執行的程式碼，例如關閉檔案和儲存狀態資訊的程式碼。</span><span class="sxs-lookup"><span data-stu-id="18224-129">The `Finalize` method can contain code that needs to execute just before an object is destroyed, such as code for closing files and saving state information.</span></span> <span data-ttu-id="18224-130">執行 `Sub Finalize` 對於效能會有些許負面影響，所以您應該只在需要明確釋放物件時才定義 `Sub Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="18224-130">There is a slight performance penalty for executing `Sub Finalize`, so you should define a `Sub Finalize` method only when you need to release objects explicitly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18224-131">在 CLR 記憶體回收行程並不會 （而且也無法） 處置*unmanaged 物件*，作業系統會在 CLR 環境外直接執行的物件。</span><span class="sxs-lookup"><span data-stu-id="18224-131">The garbage collector in the CLR does not (and cannot) dispose of *unmanaged objects*, objects that the operating system executes directly, outside the CLR environment.</span></span> <span data-ttu-id="18224-132">這是因為必須以不同的方式處置不同的 Unmanaged 物件。</span><span class="sxs-lookup"><span data-stu-id="18224-132">This is because different unmanaged objects must be disposed of in different ways.</span></span> <span data-ttu-id="18224-133">該資訊不是與 Unmanaged 物件直接相關聯；它必須位於物件的文件中。</span><span class="sxs-lookup"><span data-stu-id="18224-133">That information is not directly associated with the unmanaged object; it must be found in the documentation for the object.</span></span> <span data-ttu-id="18224-134">使用 Unmanaged 物件的類別必須以其 `Finalize` 方法處置它們。</span><span class="sxs-lookup"><span data-stu-id="18224-134">A class that uses unmanaged objects must dispose of them in its `Finalize` method.</span></span>  
  
 <span data-ttu-id="18224-135">`Finalize` 解構函式是受保護的方法，只能從其所屬的類別或衍生類別呼叫。</span><span class="sxs-lookup"><span data-stu-id="18224-135">The `Finalize` destructor is a protected method that can be called only from the class it belongs to, or from derived classes.</span></span> <span data-ttu-id="18224-136">系統會在物件被終結時自動呼叫 `Finalize`，所以您不應該從衍生類別的 `Finalize` 實作外明確地呼叫 `Finalize`。</span><span class="sxs-lookup"><span data-stu-id="18224-136">The system calls `Finalize` automatically when an object is destroyed, so you should not explicitly call `Finalize` from outside of a derived class's `Finalize` implementation.</span></span>  
  
 <span data-ttu-id="18224-137">有別於 `Class_Terminate` 會在物件未設定為任何設定時立即執行，物件失去範圍的時間與 Visual Basic 呼叫 `Finalize` 解構函式的時間之間通常會有延遲。</span><span class="sxs-lookup"><span data-stu-id="18224-137">Unlike `Class_Terminate`, which executes as soon as an object is set to nothing, there is usually a delay between when an object loses scope and when Visual Basic calls the `Finalize` destructor.</span></span> [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]<span data-ttu-id="18224-138"> 及更新版本允許第二種解構函式 <xref:System.IDisposable.Dispose%2A>，您可以隨時明確呼叫它以立即釋放資源。</span><span class="sxs-lookup"><span data-stu-id="18224-138"> and later versions allow for a second kind of destructor, <xref:System.IDisposable.Dispose%2A>, which can be explicitly called at any time to immediately release resources.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18224-139">`Finalize` 解構函式不應該擲回例外狀況，因為應用程式無法處理它們，而且可能會導致應用程式終止。</span><span class="sxs-lookup"><span data-stu-id="18224-139">A `Finalize` destructor should not throw exceptions, because they cannot be handled by the application and can cause the application to terminate.</span></span>  
  
### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a><span data-ttu-id="18224-140">新方法和 Finalize 方法在類別階層中的運作方式</span><span class="sxs-lookup"><span data-stu-id="18224-140">How New and Finalize Methods Work in a Class Hierarchy</span></span>  
 <span data-ttu-id="18224-141">每當建立類別的執行個體時，通用語言執行平台 (CLR) 會嘗試執行名為 `New` 的程序 (如果它存在於該物件)。</span><span class="sxs-lookup"><span data-stu-id="18224-141">Whenever an instance of a class is created, the common language runtime (CLR) attempts to execute a procedure named `New`, if it exists in that object.</span></span> <span data-ttu-id="18224-142">`New` 是一種稱為 `constructor` 的程序，用來在物件中的任何其他程式碼執行之前初始化新物件。</span><span class="sxs-lookup"><span data-stu-id="18224-142">`New` is a type of procedure called a `constructor` that is used to initialize new objects before any other code in an object executes.</span></span> <span data-ttu-id="18224-143">`New` 建構函式可以用來開啟檔案、連接到資料庫、初始化變數，以及處理必須先完成才能使用物件的任何其他工作。</span><span class="sxs-lookup"><span data-stu-id="18224-143">A `New` constructor can be used to open files, connect to databases, initialize variables, and take care of any other tasks that need to be done before an object can be used.</span></span>  
  
 <span data-ttu-id="18224-144">建立衍生類別的執行個體時，基底類別的 `Sub New` 的建構函式會最先執行，然後衍生類別中的建構函式接著執行。</span><span class="sxs-lookup"><span data-stu-id="18224-144">When an instance of a derived class is created, the `Sub New` constructor of the base class executes first, followed by constructors in derived classes.</span></span> <span data-ttu-id="18224-145">這是因為 `Sub New` 建構函式的程式碼中的第一行使用語法 `MyBase.New()` 呼叫在類別階層中在其本身正上方之類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="18224-145">This happens because the first line of code in a `Sub New` constructor uses the syntax `MyBase.New()`to call the constructor of the class immediately above itself in the class hierarchy.</span></span> <span data-ttu-id="18224-146">然後會針對類別階層中的每個類別呼叫 `Sub New` 建構函式，直到達到基底類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="18224-146">The `Sub New` constructor is then called for each class in the class hierarchy until the constructor for the base class is reached.</span></span> <span data-ttu-id="18224-147">此時，會執行基底類別的建構函式中的程式碼，接著執行所有衍生類別中的每個建構函式中的程式碼，最後執行最多衍生類別中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="18224-147">At that point, the code in the constructor for the base class executes, followed by the code in each constructor in all derived classes and the code in the most derived classes is executed last.</span></span>  
  
 <span data-ttu-id="18224-148">![建構函式和繼承](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance.gif "vaConstructorsInheritance")</span><span class="sxs-lookup"><span data-stu-id="18224-148">![Constructors and Inheritance](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance.gif "vaConstructorsInheritance")</span></span>  
  
 <span data-ttu-id="18224-149">當不再需要某物件時，CLR 就會針對該物件呼叫 <xref:System.Object.Finalize%2A> 方法，然後再釋放其記憶體。</span><span class="sxs-lookup"><span data-stu-id="18224-149">When an object is no longer needed, the CLR calls the <xref:System.Object.Finalize%2A> method for that object before freeing its memory.</span></span> <span data-ttu-id="18224-150"><xref:System.Object.Finalize%2A> 方法會呼叫 `destructor`、因為它會執行清理工作 (例如儲存狀態資訊、關閉檔案和連接至資料庫) 以及在釋放物件之前必須完成的其他工作。</span><span class="sxs-lookup"><span data-stu-id="18224-150">The <xref:System.Object.Finalize%2A> method is called a `destructor` because it performs cleanup tasks, such as saving state information, closing files and connections to databases, and other tasks that must be done before releasing the object.</span></span>  
  
 <span data-ttu-id="18224-151">![建構函式和繼承 2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance_2.gif "vaConstructorsInheritance_2")</span><span class="sxs-lookup"><span data-stu-id="18224-151">![Constructors Inheritance2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance_2.gif "vaConstructorsInheritance_2")</span></span>  
  
## <a name="idisposable-interface"></a><span data-ttu-id="18224-152">IDisposable 介面</span><span class="sxs-lookup"><span data-stu-id="18224-152">IDisposable Interface</span></span>  
 <span data-ttu-id="18224-153">類別執行個體經常會控制不受 CLR 管理的資源，例如 Windows 控制代碼和資料庫連線。</span><span class="sxs-lookup"><span data-stu-id="18224-153">Class instances often control resources not managed by the CLR, such as Windows handles and database connections.</span></span> <span data-ttu-id="18224-154">這些資源必須在類別的 `Finalize` 方法中處置，這樣在記憶體回收行程終結物件時就會釋放它們。</span><span class="sxs-lookup"><span data-stu-id="18224-154">These resources must be disposed of in the `Finalize` method of the class, so that they will be released when the object is destroyed by the garbage collector.</span></span> <span data-ttu-id="18224-155">然而，記憶體回收行程只會在 CLR 需要更多的可用記憶體時才會終結物件。</span><span class="sxs-lookup"><span data-stu-id="18224-155">However, the garbage collector destroys objects only when the CLR requires more free memory.</span></span> <span data-ttu-id="18224-156">這表示在物件超出範圍之前可能不會釋放資源。</span><span class="sxs-lookup"><span data-stu-id="18224-156">This means that the resources may not be released until long after the object goes out of scope.</span></span>  
  
 <span data-ttu-id="18224-157">為了補充記憶體回收，您的類別可以提供機制以主動管理系統資源，不過前提是它們實作 <xref:System.IDisposable> 介面。</span><span class="sxs-lookup"><span data-stu-id="18224-157">To supplement garbage collection, your classes can provide a mechanism to actively manage system resources if they implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="18224-158"><xref:System.IDisposable> 具有 <xref:System.IDisposable.Dispose%2A> 這種方法，當用戶端完成使用物件時，它們應該加以呼叫。</span><span class="sxs-lookup"><span data-stu-id="18224-158"><xref:System.IDisposable> has one method, <xref:System.IDisposable.Dispose%2A>, which clients should call when they finish using an object.</span></span> <span data-ttu-id="18224-159">您可以使用 <xref:System.IDisposable.Dispose%2A> 方法立即釋放資源及執行工作，例如關閉檔案和資料庫連線。</span><span class="sxs-lookup"><span data-stu-id="18224-159">You can use the <xref:System.IDisposable.Dispose%2A> method to immediately release resources and perform tasks such as closing files and database connections.</span></span> <span data-ttu-id="18224-160">與 `Finalize` 解構函式不同的是，不會自動呼叫 <xref:System.IDisposable.Dispose%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="18224-160">Unlike the `Finalize` destructor, the <xref:System.IDisposable.Dispose%2A> method is not called automatically.</span></span> <span data-ttu-id="18224-161">當您想要立即釋放資源時，類別的用戶端必須明確地呼叫 <xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="18224-161">Clients of a class must explicitly call <xref:System.IDisposable.Dispose%2A> when you want to immediately release resources.</span></span>  
  
### <a name="implementing-idisposable"></a><span data-ttu-id="18224-162">實作 IDisposable</span><span class="sxs-lookup"><span data-stu-id="18224-162">Implementing IDisposable</span></span>  
 <span data-ttu-id="18224-163">實作 <xref:System.IDisposable> 介面的類別應該包含以下幾段程式碼：</span><span class="sxs-lookup"><span data-stu-id="18224-163">A class that implements the <xref:System.IDisposable> interface should include these sections of code:</span></span>  
  
-   <span data-ttu-id="18224-164">追蹤是否已處置物件的欄位：</span><span class="sxs-lookup"><span data-stu-id="18224-164">A field for keeping track of whether the object has been disposed:</span></span>  
  
    ```  
    Protected disposed As Boolean = False  
    ```  
  
-   <span data-ttu-id="18224-165"><xref:System.IDisposable.Dispose%2A> 多載，會釋放該類別的資源。</span><span class="sxs-lookup"><span data-stu-id="18224-165">An overload of the <xref:System.IDisposable.Dispose%2A> that frees the class's resources.</span></span> <span data-ttu-id="18224-166">這個方法應該由基底類別的 <xref:System.IDisposable.Dispose%2A> 和 `Finalize` 方法呼叫：</span><span class="sxs-lookup"><span data-stu-id="18224-166">This method should be called by the <xref:System.IDisposable.Dispose%2A> and `Finalize` methods of the base class:</span></span>  
  
    ```  
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
  
-   <span data-ttu-id="18224-167">僅包含下列程式碼的 <xref:System.IDisposable.Dispose%2A> 實作：</span><span class="sxs-lookup"><span data-stu-id="18224-167">An implementation of <xref:System.IDisposable.Dispose%2A> that contains only the following code:</span></span>  
  
    ```  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
    ```  
  
-   <span data-ttu-id="18224-168">僅包含下列程式碼的 `Finalize` 方法置換：</span><span class="sxs-lookup"><span data-stu-id="18224-168">An override of the `Finalize` method that contains only the following code:</span></span>  
  
    ```  
    Protected Overrides Sub Finalize()  
        Dispose(False)  
        MyBase.Finalize()  
    End Sub  
    ```  
  
### <a name="deriving-from-a-class-that-implements-idisposable"></a><span data-ttu-id="18224-169">從實作 IDisposable 的類別衍生</span><span class="sxs-lookup"><span data-stu-id="18224-169">Deriving from a Class that Implements IDisposable</span></span>  
 <span data-ttu-id="18224-170">從實作 <xref:System.IDisposable> 介面之基底類別衍生的類別不需要覆寫任何基底方法，除非它使用需要處置的其他資源。</span><span class="sxs-lookup"><span data-stu-id="18224-170">A class that derives from a base class that implements the <xref:System.IDisposable> interface does not need to override any of the base methods unless it uses additional resources that need to be disposed.</span></span> <span data-ttu-id="18224-171">在該情況下，衍生的類別應該覆寫基底類別的 `Dispose(disposing)` 方法來處置衍生類別的資源。</span><span class="sxs-lookup"><span data-stu-id="18224-171">In that situation, the derived class should override the base class's `Dispose(disposing)` method to dispose of the derived class's resources.</span></span> <span data-ttu-id="18224-172">這個覆寫必須呼叫基底類別的 `Dispose(disposing)` 方法。</span><span class="sxs-lookup"><span data-stu-id="18224-172">This override must call the base class's `Dispose(disposing)` method.</span></span>  
  
```  
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
  
 <span data-ttu-id="18224-173">衍生類別不應該覆寫基底類別的 <xref:System.IDisposable.Dispose%2A> 和 `Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="18224-173">A derived class should not override the base class's <xref:System.IDisposable.Dispose%2A> and `Finalize` methods.</span></span> <span data-ttu-id="18224-174">從衍生類別的執行個體呼叫那些方法時，基底類別對於那些方法的實作會呼叫衍生類別的 `Dispose(disposing)` 方法覆寫。</span><span class="sxs-lookup"><span data-stu-id="18224-174">When those methods are called from an instance of the derived class, the base class's implementation of those methods call the derived class's override of the `Dispose(disposing)` method.</span></span>  
  
## <a name="garbage-collection-and-the-finalize-destructor"></a><span data-ttu-id="18224-175">記憶體回收和 Finalize 解構函式</span><span class="sxs-lookup"><span data-stu-id="18224-175">Garbage Collection and the Finalize Destructor</span></span>  
 <span data-ttu-id="18224-176">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]會使用*參考 reference-tracing garbage collection*系統，定期釋放未使用的資源。</span><span class="sxs-lookup"><span data-stu-id="18224-176">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uses the *reference-tracing garbage collection* system to periodically release unused resources.</span></span> <span data-ttu-id="18224-177">Visual Basic 6.0 和更早版本使用不同的系統，稱為*參考計數*來管理資源。</span><span class="sxs-lookup"><span data-stu-id="18224-177">Visual Basic 6.0 and earlier versions used a different system called *reference counting* to manage resources.</span></span> <span data-ttu-id="18224-178">這兩個系統固然會自動執行相同的功能，不過有幾個重要的差異。</span><span class="sxs-lookup"><span data-stu-id="18224-178">Although both systems perform the same function automatically, there are a few important differences.</span></span>  
  
 <span data-ttu-id="18224-179">當系統決定不再需要這類物件時，CLR 會定期終結該物件。</span><span class="sxs-lookup"><span data-stu-id="18224-179">The CLR periodically destroys objects when the system determines that such objects are no longer needed.</span></span> <span data-ttu-id="18224-180">當系統資源短缺時，會更快釋放物件，反之則較不常釋放物件。</span><span class="sxs-lookup"><span data-stu-id="18224-180">Objects are released more quickly when system resources are in short supply, and less frequently otherwise.</span></span> <span data-ttu-id="18224-181">物件失去範圍的時間與 CLR 釋放它的時間之間的延遲表示，與 Visual Basic 6.0 及舊版中的物件不同的是，您無法精確判斷何時將會終結物件。</span><span class="sxs-lookup"><span data-stu-id="18224-181">The delay between when an object loses scope and when the CLR releases it means that, unlike with objects in Visual Basic 6.0 and earlier versions, you cannot determine exactly when the object will be destroyed.</span></span> <span data-ttu-id="18224-182">在這種情況下，物件被視為具有*不具決定性存留期*。</span><span class="sxs-lookup"><span data-stu-id="18224-182">In such a situation, objects are said to have *non-deterministic lifetime*.</span></span> <span data-ttu-id="18224-183">在大部分的情況下，不具決定性存留期不會變更撰寫應用程式的方式，只要記住，`Finalize` 解構函式可能不會在物件失去範圍時立即執行。</span><span class="sxs-lookup"><span data-stu-id="18224-183">In most cases, non-deterministic lifetime does not change how you write applications, as long as you remember that the `Finalize` destructor may not immediately execute when an object loses scope.</span></span>  
  
 <span data-ttu-id="18224-184">記憶體回收系統之間的另一個差異牽涉到使用 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="18224-184">Another difference between the garbage-collection systems involves the use of `Nothing`.</span></span> <span data-ttu-id="18224-185">若要利用 Visual Basic 6.0 及舊版中的參考計數，程式設計師有時候會將 `Nothing` 指派給物件變數，以釋放那些變數所保留的參考。</span><span class="sxs-lookup"><span data-stu-id="18224-185">To take advantage of reference counting in Visual Basic 6.0 and earlier versions, programmers sometimes assigned `Nothing` to object variables to release the references those variables held.</span></span> <span data-ttu-id="18224-186">如果變數保留物件的最後參考，就會立即釋放物件資源。</span><span class="sxs-lookup"><span data-stu-id="18224-186">If the variable held the last reference to the object, the object's resources were released immediately.</span></span> <span data-ttu-id="18224-187">在新版 Visual Basic 中，雖然可能在一些情況下，此程序仍相當重要，但是執行它永遠不會造成參考的物件立即釋放其資源。</span><span class="sxs-lookup"><span data-stu-id="18224-187">In later versions of Visual Basic, while there may be cases in which this procedure is still valuable, performing it never causes the referenced object to release its resources immediately.</span></span> <span data-ttu-id="18224-188">若要立即釋放資源，請使用物件的 <xref:System.IDisposable.Dispose%2A> 方法 (若有的話)。</span><span class="sxs-lookup"><span data-stu-id="18224-188">To release resources immediately, use the object's <xref:System.IDisposable.Dispose%2A> method, if available.</span></span> <span data-ttu-id="18224-189">唯一應該將變數設定為 `Nothing` 的時間，是在它的存留期相對於記憶體回收行程偵測失去關聯之物件所需的時間較長時。</span><span class="sxs-lookup"><span data-stu-id="18224-189">The only time you should set a variable to `Nothing` is when its lifetime is long relative to the time the garbage collector takes to detect orphaned objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18224-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18224-190">See Also</span></span>  
 <xref:System.IDisposable.Dispose%2A>  
 [<span data-ttu-id="18224-191">初始化及終止元件</span><span class="sxs-lookup"><span data-stu-id="18224-191">Initialization and Termination of Components</span></span>](http://msdn.microsoft.com/library/58444076-a9d2-4c91-b3f6-0e180dc0695d)  
 [<span data-ttu-id="18224-192">New 運算子</span><span class="sxs-lookup"><span data-stu-id="18224-192">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="18224-193">清除 Unmanaged 資源</span><span class="sxs-lookup"><span data-stu-id="18224-193">Cleaning Up Unmanaged Resources</span></span>](../../../../standard/garbage-collection/unmanaged.md)  
 [<span data-ttu-id="18224-194">Nothing</span><span class="sxs-lookup"><span data-stu-id="18224-194">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
