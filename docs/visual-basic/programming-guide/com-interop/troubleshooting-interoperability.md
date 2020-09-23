---
title: 疑難排解互通性的問題
ms.date: 07/20/2015
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability [Visual Basic]
- interoperability, troubleshooting
- COM interop [Visual Basic], troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
ms.openlocfilehash: 135b121638b92adc5a3b0920aa29d10fd1d62d14
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075989"
---
# <a name="troubleshooting-interoperability-visual-basic"></a><span data-ttu-id="31c48-102">疑難排解互通性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31c48-102">Troubleshooting Interoperability (Visual Basic)</span></span>

<span data-ttu-id="31c48-103">當您在 COM 和 .NET Framework 的 managed 程式碼之間交互操作時，您可能會遇到下列一或多個常見的問題。</span><span class="sxs-lookup"><span data-stu-id="31c48-103">When you interoperate between COM and the managed code of the .NET Framework, you may encounter one or more of the following common issues.</span></span>  
  
## <a name="interop-marshaling"></a><a name="vbconinteroperabilitymarshalinganchor1"></a> <span data-ttu-id="31c48-104">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="31c48-104">Interop Marshaling</span></span>  

 <span data-ttu-id="31c48-105">有時，您可能必須使用不屬於 .NET Framework 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="31c48-105">At times, you may have to use data types that are not part of the .NET Framework.</span></span> <span data-ttu-id="31c48-106">Interop 元件會處理 COM 物件的大部分工作，但是您可能必須控制在 managed 物件公開至 COM 時所使用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="31c48-106">Interop assemblies handle most of the work for COM objects, but you may have to control the data types that are used when managed objects are exposed to COM.</span></span> <span data-ttu-id="31c48-107">例如，類別庫中的結構必須 `BStr` 在傳送給 Visual Basic 6.0 和較早版本所建立之 COM 物件的字串上指定非受控型別。</span><span class="sxs-lookup"><span data-stu-id="31c48-107">For example, structures in class libraries must specify the `BStr` unmanaged type on strings sent to COM objects created by Visual Basic 6.0 and earlier versions.</span></span> <span data-ttu-id="31c48-108">在這種情況下，您可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，使 managed 類型公開為非受控類型。</span><span class="sxs-lookup"><span data-stu-id="31c48-108">In such cases, you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to cause managed types to be exposed as unmanaged types.</span></span>  
  
## <a name="exporting-fixed-length-strings-to-unmanaged-code"></a><a name="vbconinteroperabilitymarshalinganchor2"></a> <span data-ttu-id="31c48-109">將固定長度的字串匯出至非受控碼</span><span class="sxs-lookup"><span data-stu-id="31c48-109">Exporting Fixed-Length Strings to Unmanaged Code</span></span>  

 <span data-ttu-id="31c48-110">在 Visual Basic 6.0 及更早版本中，字串會以不含 null 終止字元的位元組序列形式匯出至 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="31c48-110">In Visual Basic 6.0 and earlier versions, strings are exported to COM objects as sequences of bytes without a null termination character.</span></span> <span data-ttu-id="31c48-111">為了與其他語言相容，Visual Basic .NET 會在匯出字串時包含終止字元。</span><span class="sxs-lookup"><span data-stu-id="31c48-111">For compatibility with other languages, Visual Basic .NET includes a termination character when exporting strings.</span></span> <span data-ttu-id="31c48-112">解決此不相容性的最佳方式，是將缺少終止字元的字串匯出為或的陣列 `Byte` `Char` 。</span><span class="sxs-lookup"><span data-stu-id="31c48-112">The best way to address this incompatibility is to export strings that lack the termination character as arrays of `Byte` or `Char`.</span></span>  
  
## <a name="exporting-inheritance-hierarchies"></a><a name="vbconinteroperabilitymarshalinganchor3"></a> <span data-ttu-id="31c48-113">正在匯出繼承階層</span><span class="sxs-lookup"><span data-stu-id="31c48-113">Exporting Inheritance Hierarchies</span></span>  

 <span data-ttu-id="31c48-114">Managed 類別階層會在公開為 COM 物件時壓平合併。</span><span class="sxs-lookup"><span data-stu-id="31c48-114">Managed class hierarchies flatten out when exposed as COM objects.</span></span> <span data-ttu-id="31c48-115">例如，如果您定義具有成員的基類，然後在公開為 COM 物件的衍生類別中繼承基類，則在 COM 物件中使用衍生類別的用戶端將無法使用繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="31c48-115">For example, if you define a base class with a member, and then inherit the base class in a derived class that is exposed as a COM object, clients that use the derived class in the COM object will not be able to use the inherited members.</span></span> <span data-ttu-id="31c48-116">基類成員只能從 COM 物件存取為基類的實例，而且只有在基類也建立為 COM 物件時才可存取。</span><span class="sxs-lookup"><span data-stu-id="31c48-116">Base class members can be accessed from COM objects only as instances of a base class, and then only if the base class is also created as a COM object.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="31c48-117">多載方法</span><span class="sxs-lookup"><span data-stu-id="31c48-117">Overloaded Methods</span></span>  

 <span data-ttu-id="31c48-118">雖然您可以使用 Visual Basic 建立多載的方法，但 COM 並不支援它們。</span><span class="sxs-lookup"><span data-stu-id="31c48-118">Although you can create overloaded methods with Visual Basic, they are not supported by COM.</span></span> <span data-ttu-id="31c48-119">當包含多載方法的類別公開為 COM 物件時，會為多載方法產生新的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="31c48-119">When a class that contains overloaded methods is exposed as a COM object, new method names are generated for the overloaded methods.</span></span>  
  
 <span data-ttu-id="31c48-120">例如，假設有一個類別具有兩個方法的多載 `Synch` 。</span><span class="sxs-lookup"><span data-stu-id="31c48-120">For example, consider a class that has two overloads of the `Synch` method.</span></span> <span data-ttu-id="31c48-121">當類別公開為 COM 物件時，新產生的方法名稱可能是 `Synch` 和 `Synch_2` 。</span><span class="sxs-lookup"><span data-stu-id="31c48-121">When the class is exposed as a COM object, the new generated method names could be `Synch` and `Synch_2`.</span></span>  
  
 <span data-ttu-id="31c48-122">重新命名可能會對 COM 物件的取用者造成兩個問題。</span><span class="sxs-lookup"><span data-stu-id="31c48-122">The renaming can cause two problems for consumers of the COM object.</span></span>  
  
1. <span data-ttu-id="31c48-123">用戶端可能不會預期產生的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="31c48-123">Clients might not expect the generated method names.</span></span>  
  
2. <span data-ttu-id="31c48-124">當新的多載加入至類別或其基類時，公開為 COM 物件的類別中所產生的方法名稱可能會變更。</span><span class="sxs-lookup"><span data-stu-id="31c48-124">The generated method names in the class exposed as a COM object can change when new overloads are added to the class or its base class.</span></span> <span data-ttu-id="31c48-125">這可能會導致版本控制問題。</span><span class="sxs-lookup"><span data-stu-id="31c48-125">This can cause versioning problems.</span></span>  
  
 <span data-ttu-id="31c48-126">若要解決這兩個問題，請在開發將公開為 COM 物件的物件時，為每個方法提供唯一的名稱，而非使用多載。</span><span class="sxs-lookup"><span data-stu-id="31c48-126">To solve both problems, give each method a unique name, instead of using overloading, when you develop objects that will be exposed as COM objects.</span></span>  
  
## <a name="use-of-com-objects-through-interop-assemblies"></a><a name="vbconinteroperabilitymarshalinganchor4"></a> <span data-ttu-id="31c48-127">透過 Interop 元件使用 COM 物件</span><span class="sxs-lookup"><span data-stu-id="31c48-127">Use of COM Objects Through Interop Assemblies</span></span>  

 <span data-ttu-id="31c48-128">您可以使用 interop 元件，就像是它們所代表之 COM 物件的 managed 程式碼取代一樣。</span><span class="sxs-lookup"><span data-stu-id="31c48-128">You use interop assemblies almost as if they are managed code replacements for the COM objects they represent.</span></span> <span data-ttu-id="31c48-129">不過，由於它們是包裝函式，而不是實際的 COM 物件，因此使用 interop 元件和標準元件之間有一些差異。</span><span class="sxs-lookup"><span data-stu-id="31c48-129">However, because they are wrappers and not actual COM objects, there are some differences between using interop assemblies and standard assemblies.</span></span> <span data-ttu-id="31c48-130">這些差異區域包括類別的公開，以及參數和傳回值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="31c48-130">These areas of difference include the exposure of classes, and data types for parameters and return values.</span></span>  
  
## <a name="classes-exposed-as-both-interfaces-and-classes"></a><a name="vbconinteroperabilitymarshalinganchor5"></a> <span data-ttu-id="31c48-131">公開為介面和類別的類別</span><span class="sxs-lookup"><span data-stu-id="31c48-131">Classes Exposed as Both Interfaces and Classes</span></span>  

 <span data-ttu-id="31c48-132">不同于標準元件中的類別，COM 類別會在 interop 元件中公開為介面和表示 COM 類別的類別。</span><span class="sxs-lookup"><span data-stu-id="31c48-132">Unlike classes in standard assemblies, COM classes are exposed in interop assemblies as both an interface and a class that represents the COM class.</span></span> <span data-ttu-id="31c48-133">介面的名稱與 COM 類別的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="31c48-133">The interface's name is identical to that of the COM class.</span></span> <span data-ttu-id="31c48-134">Interop 類別的名稱與原始 COM 類別的名稱相同，但附加了 "Class" 這個字。</span><span class="sxs-lookup"><span data-stu-id="31c48-134">The name of the interop class is the same as that of the original COM class, but with the word "Class" appended.</span></span> <span data-ttu-id="31c48-135">例如，假設您有一個具有 COM 物件之 interop 元件參考的專案。</span><span class="sxs-lookup"><span data-stu-id="31c48-135">For example, suppose you have a project with a reference to an interop assembly for a COM object.</span></span> <span data-ttu-id="31c48-136">如果 COM 類別命名為 `MyComClass` ，IntelliSense 和物件瀏覽器會顯示名為的介面， `MyComClass` 以及名為的類別 `MyComClassClass` 。</span><span class="sxs-lookup"><span data-stu-id="31c48-136">If the COM class is named `MyComClass`, IntelliSense and the Object Browser show an interface named `MyComClass` and a class named `MyComClassClass`.</span></span>  
  
## <a name="creating-instances-of-a-net-framework-class"></a><a name="vbconinteroperabilitymarshalinganchor6"></a> <span data-ttu-id="31c48-137">建立 .NET Framework 類別的實例</span><span class="sxs-lookup"><span data-stu-id="31c48-137">Creating Instances of a .NET Framework Class</span></span>  

 <span data-ttu-id="31c48-138">一般來說，您會使用具有類別名稱的語句來建立 .NET Framework 類別的實例 `New` 。</span><span class="sxs-lookup"><span data-stu-id="31c48-138">Generally, you create an instance of a .NET Framework class using the `New` statement with a class name.</span></span> <span data-ttu-id="31c48-139">具有 interop 元件表示的 COM 類別，是您可以使用語句搭配介面的一種情況 `New` 。</span><span class="sxs-lookup"><span data-stu-id="31c48-139">Having a COM class represented by an interop assembly is the one case in which you can use the `New` statement with an interface.</span></span> <span data-ttu-id="31c48-140">除非您使用 COM 類別搭配 `Inherits` 語句，否則您可以使用介面，就像使用類別一樣。</span><span class="sxs-lookup"><span data-stu-id="31c48-140">Unless you are using the COM class with an `Inherits` statement, you can use the interface just as you would a class.</span></span> <span data-ttu-id="31c48-141">下列程式碼示範如何 `Command` 在專案中建立物件，該物件具有 Microsoft ActiveX Data Objects 2.8 程式庫 COM 物件的參考：</span><span class="sxs-lookup"><span data-stu-id="31c48-141">The following code demonstrates how to create a `Command` object in a project that has a reference to the Microsoft ActiveX Data Objects 2.8 Library COM object:</span></span>  
  
 [!code-vb[VbVbalrInterop#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#20)]  
  
 <span data-ttu-id="31c48-142">但是，如果您使用 COM 類別做為衍生類別的基底，您必須使用表示 COM 類別的 interop 類別，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="31c48-142">However, if you are using the COM class as the base for a derived class, you must use the interop class that represents the COM class, as in the following code:</span></span>  
  
 [!code-vb[VbVbalrInterop#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#21)]  
  
> [!NOTE]
> <span data-ttu-id="31c48-143">Interop 元件會隱含地執行表示 COM 類別的介面。</span><span class="sxs-lookup"><span data-stu-id="31c48-143">Interop assemblies implicitly implement interfaces that represent COM classes.</span></span> <span data-ttu-id="31c48-144">您不應該嘗試使用 `Implements` 語句來執行這些介面，否則就會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="31c48-144">You should not try to use the `Implements` statement to implement these interfaces or an error will result.</span></span>  
  
## <a name="data-types-for-parameters-and-return-values"></a><a name="vbconinteroperabilitymarshalinganchor7"></a> <span data-ttu-id="31c48-145">參數和傳回值的資料類型</span><span class="sxs-lookup"><span data-stu-id="31c48-145">Data Types for Parameters and Return Values</span></span>  

 <span data-ttu-id="31c48-146">不同于標準元件的成員，interop 元件成員的資料類型可能與原始物件宣告中所用的不同。</span><span class="sxs-lookup"><span data-stu-id="31c48-146">Unlike members of standard assemblies, interop assembly members may have data types that differ from those used in the  original object declaration.</span></span> <span data-ttu-id="31c48-147">雖然 interop 元件會以隱含方式將 COM 類型轉換成相容的 common language runtime 型別，但是您應該注意這兩個邊所使用的資料類型，以防止執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="31c48-147">Although interop assemblies implicitly convert COM types to compatible common language runtime types, you should pay attention to the data types that are used by both sides to prevent runtime errors.</span></span> <span data-ttu-id="31c48-148">例如，在 Visual Basic 6.0 和較早版本所建立的 COM 物件中，型別的值會 `Integer` 假設 .NET Framework 對等型別 `Short` 。</span><span class="sxs-lookup"><span data-stu-id="31c48-148">For example, in COM objects created in Visual Basic 6.0 and earlier versions, values of type `Integer` assume the .NET Framework equivalent type, `Short`.</span></span> <span data-ttu-id="31c48-149">建議您在使用匯入的成員之前，先使用物件瀏覽器來檢查其特性。</span><span class="sxs-lookup"><span data-stu-id="31c48-149">It is recommended that you use the Object Browser to examine the characteristics of imported members before you use them.</span></span>  
  
## <a name="module-level-com-methods"></a><a name="vbconinteroperabilitymarshalinganchor8"></a> <span data-ttu-id="31c48-150">模組層級 COM 方法</span><span class="sxs-lookup"><span data-stu-id="31c48-150">Module level COM methods</span></span>  

 <span data-ttu-id="31c48-151">大部分 COM 物件的使用方式是使用關鍵字來建立 COM 類別的實例 `New` ，然後呼叫物件的方法。</span><span class="sxs-lookup"><span data-stu-id="31c48-151">Most COM objects are used by creating an instance of a COM class using the `New` keyword and then calling methods of the object.</span></span> <span data-ttu-id="31c48-152">這項規則的例外狀況包括包含 `AppObj` 或 com 類別的 com 物件 `GlobalMultiUse` 。</span><span class="sxs-lookup"><span data-stu-id="31c48-152">One exception to this rule involves COM objects that contain `AppObj` or `GlobalMultiUse` COM classes.</span></span> <span data-ttu-id="31c48-153">這類類別與 Visual Basic .NET 類別中的模組層級方法類似。</span><span class="sxs-lookup"><span data-stu-id="31c48-153">Such classes resemble module level methods in Visual Basic .NET classes.</span></span> <span data-ttu-id="31c48-154">當您第一次呼叫其中一個方法時，Visual Basic 6.0 及更早版本會隱含地為您建立這類物件的實例。</span><span class="sxs-lookup"><span data-stu-id="31c48-154">Visual Basic 6.0 and earlier versions implicitly create instances of such objects for you the first time that you call one of their methods.</span></span> <span data-ttu-id="31c48-155">例如，在 Visual Basic 6.0 中，您可以新增 Microsoft DAO 3.6 物件程式庫的參考，並呼叫 `DBEngine` 方法，而不需要先建立實例：</span><span class="sxs-lookup"><span data-stu-id="31c48-155">For example, in Visual Basic 6.0 you can add a reference to the Microsoft DAO 3.6 Object Library and call the `DBEngine` method without first creating an instance:</span></span>  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 <span data-ttu-id="31c48-156">Visual Basic .NET 需要您一律先建立 COM 物件的實例，才能使用其方法。</span><span class="sxs-lookup"><span data-stu-id="31c48-156">Visual Basic .NET requires that you always create instances of COM objects before you can use their methods.</span></span> <span data-ttu-id="31c48-157">若要在 Visual Basic 中使用這些方法，請宣告所需類別的變數，並使用 new 關鍵字將物件指派給物件變數。</span><span class="sxs-lookup"><span data-stu-id="31c48-157">To use these methods in Visual Basic, declare a variable of the desired class and use the new keyword to assign the object to the object variable.</span></span> <span data-ttu-id="31c48-158">`Shared`當您想要確保只建立類別的一個實例時，可以使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="31c48-158">The `Shared` keyword can be used when you want to make sure that only one instance of the class is created.</span></span>  
  
 [!code-vb[VbVbalrInterop#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#23)]  
  
## <a name="unhandled-errors-in-event-handlers"></a><a name="vbconinteroperabilitymarshalinganchor9"></a> <span data-ttu-id="31c48-159">事件處理常式中的未處理錯誤</span><span class="sxs-lookup"><span data-stu-id="31c48-159">Unhandled Errors in Event Handlers</span></span>  

 <span data-ttu-id="31c48-160">其中一個常見的 interop 問題牽涉到事件處理常式中的錯誤，這些錯誤會處理 COM 物件所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="31c48-160">One common interop problem involves errors in event handlers that handle events raised by COM objects.</span></span> <span data-ttu-id="31c48-161">除非您使用或語句來明確檢查錯誤，否則會忽略這類錯誤 `On Error` `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="31c48-161">Such errors are ignored unless you specifically check for errors using `On Error` or `Try...Catch...Finally` statements.</span></span> <span data-ttu-id="31c48-162">例如，下列範例是來自具有 Microsoft ActiveX Data Objects 2.8 程式庫 COM 物件參考的 Visual Basic .NET 專案。</span><span class="sxs-lookup"><span data-stu-id="31c48-162">For example, the following example is from a Visual Basic .NET project that has a reference to the Microsoft ActiveX Data Objects 2.8 Library COM object.</span></span>  
  
 [!code-vb[VbVbalrInterop#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#24)]  
  
 <span data-ttu-id="31c48-163">此範例會如預期般引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="31c48-163">This example raises an error as expected.</span></span> <span data-ttu-id="31c48-164">但是，如果您在沒有區塊的情況下嘗試相同的範例 `Try...Catch...Finally` ，就會忽略此錯誤，就像您使用 `OnError Resume Next` 語句一樣。</span><span class="sxs-lookup"><span data-stu-id="31c48-164">However, if you try the same example without the `Try...Catch...Finally` block, the error is ignored as if you used the `OnError Resume Next` statement.</span></span> <span data-ttu-id="31c48-165">如果沒有錯誤處理，則零除的無訊息模式會失敗。</span><span class="sxs-lookup"><span data-stu-id="31c48-165">Without error handling, the division by zero silently fails.</span></span> <span data-ttu-id="31c48-166">因為這類錯誤永遠不會引發未處理的例外狀況錯誤，所以請務必在處理來自 COM 物件之事件的事件處理常式中，使用某種形式的例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="31c48-166">Because such errors never raise unhandled exception errors, it is important that you use some form of exception handling in event handlers that handle events from COM objects.</span></span>  
  
### <a name="understanding-com-interop-errors"></a><span data-ttu-id="31c48-167">瞭解 COM interop 錯誤</span><span class="sxs-lookup"><span data-stu-id="31c48-167">Understanding COM interop errors</span></span>  

 <span data-ttu-id="31c48-168">如果沒有錯誤處理，interop 呼叫通常會產生錯誤，提供少量的資訊。</span><span class="sxs-lookup"><span data-stu-id="31c48-168">Without error handling, interop calls often generate errors that provide little information.</span></span> <span data-ttu-id="31c48-169">可能的話，請使用結構化錯誤處理來提供問題發生時的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="31c48-169">Whenever possible, use structured error handling to provide more information about problems when they occur.</span></span> <span data-ttu-id="31c48-170">當您對應用程式進行偵錯工具時，這會特別有用。</span><span class="sxs-lookup"><span data-stu-id="31c48-170">This can be especially helpful when you debug applications.</span></span> <span data-ttu-id="31c48-171">例如：</span><span class="sxs-lookup"><span data-stu-id="31c48-171">For example:</span></span>  
  
 [!code-vb[VbVbalrInterop#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#25)]  
  
 <span data-ttu-id="31c48-172">您可以藉由檢查例外狀況物件的內容，找到錯誤描述、HRESULT 和 COM 錯誤來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="31c48-172">You can find information such as the error description, HRESULT, and the source of COM errors by examining the contents of the exception object.</span></span>  
  
## <a name="activex-control-issues"></a><a name="vbconinteroperabilitymarshalinganchor10"></a> <span data-ttu-id="31c48-173">ActiveX 控制項問題</span><span class="sxs-lookup"><span data-stu-id="31c48-173">ActiveX Control Issues</span></span>  

 <span data-ttu-id="31c48-174">大部分適用于 Visual Basic 6.0 的 ActiveX 控制項都能搭配 Visual Basic 的 .NET 運作，而不會發生問題。</span><span class="sxs-lookup"><span data-stu-id="31c48-174">Most ActiveX controls that work with Visual Basic 6.0 work with Visual Basic .NET without trouble.</span></span> <span data-ttu-id="31c48-175">主要的例外狀況是容器控制項，或是以視覺化方式包含其他控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="31c48-175">The main exceptions are container controls, or controls that visually contain other controls.</span></span> <span data-ttu-id="31c48-176">某些較舊的控制項範例無法搭配 Visual Studio 正確運作，如下所示：</span><span class="sxs-lookup"><span data-stu-id="31c48-176">Some examples of older controls that do not work correctly with Visual Studio are as follows:</span></span>  
  
- <span data-ttu-id="31c48-177">Microsoft Forms 2.0 框架控制項</span><span class="sxs-lookup"><span data-stu-id="31c48-177">Microsoft Forms 2.0 Frame control</span></span>  
  
- <span data-ttu-id="31c48-178">由上而下的控制項（也稱為微調控制項）</span><span class="sxs-lookup"><span data-stu-id="31c48-178">Up-Down control, also known as the spin control</span></span>  
  
- <span data-ttu-id="31c48-179">Sheridan 索引標籤控制項</span><span class="sxs-lookup"><span data-stu-id="31c48-179">Sheridan Tab Control</span></span>  
  
 <span data-ttu-id="31c48-180">針對不支援的 ActiveX 控制項問題，只有一些因應措施。</span><span class="sxs-lookup"><span data-stu-id="31c48-180">There are only a few workarounds for unsupported ActiveX control problems.</span></span> <span data-ttu-id="31c48-181">如果您擁有原始原始程式碼，您可以將現有的控制項遷移至 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="31c48-181">You can migrate existing controls to Visual Studio if you own the original source code.</span></span> <span data-ttu-id="31c48-182">否則，您可以向軟體廠商確認是否已更新。用來取代不支援的 ActiveX 控制項之控制項的 .NET 相容版本。</span><span class="sxs-lookup"><span data-stu-id="31c48-182">Otherwise, you can check with software vendors for updated .NET-compatible versions of controls to replace unsupported ActiveX controls.</span></span>  
  
## <a name="passing-readonly-properties-of-controls-byref"></a><a name="vbconinteroperabilitymarshalinganchor11"></a> <span data-ttu-id="31c48-183">傳遞控制項的 ReadOnly 屬性 ByRef</span><span class="sxs-lookup"><span data-stu-id="31c48-183">Passing ReadOnly Properties of Controls ByRef</span></span>  

 <span data-ttu-id="31c48-184">當您將 `ReadOnly` 某些舊版 ActiveX 控制項的屬性傳遞至其他程式的參數時，Visual Basic .net 有時會引發 COM 錯誤，例如「錯誤 0x800A017F CTL_E_SETNOTSUPPORTED」 `ByRef` 。</span><span class="sxs-lookup"><span data-stu-id="31c48-184">Visual Basic .NET sometimes raises COM errors such as, "Error 0x800A017F CTL_E_SETNOTSUPPORTED", when you pass `ReadOnly` properties of some older ActiveX controls as `ByRef` parameters to other procedures.</span></span> <span data-ttu-id="31c48-185">從 Visual Basic 6.0 的類似程序呼叫不會引發錯誤，而且會將參數視為您以傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="31c48-185">Similar procedure calls from Visual Basic 6.0 do not raise an error, and the parameters are treated as if you passed them by value.</span></span> <span data-ttu-id="31c48-186">Visual Basic .NET 錯誤訊息指出您嘗試變更的屬性沒有屬性程式 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="31c48-186">The Visual Basic .NET error message indicates that you are trying to change a property that does not have a property `Set` procedure.</span></span>  
  
 <span data-ttu-id="31c48-187">如果您可以存取所呼叫的程式，您可以使用 `ByVal` 關鍵字來宣告接受屬性的參數，以避免此錯誤 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="31c48-187">If you have access to the procedure being called, you can prevent this error by using the `ByVal` keyword to declare parameters that accept `ReadOnly` properties.</span></span> <span data-ttu-id="31c48-188">例如：</span><span class="sxs-lookup"><span data-stu-id="31c48-188">For example:</span></span>  
  
 [!code-vb[VbVbalrInterop#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#26)]  
  
 <span data-ttu-id="31c48-189">如果您無法存取所呼叫之程式的原始程式碼，您可以在呼叫程式前後加上一組額外的括弧，以強制以傳值方式傳遞屬性。</span><span class="sxs-lookup"><span data-stu-id="31c48-189">If you do not have access to the source code for the procedure being called, you can force the property to be passed by value by adding an extra set of brackets around the calling procedure.</span></span> <span data-ttu-id="31c48-190">例如，在具有 Microsoft ActiveX Data Objects 2.8 程式庫 COM 物件參考的專案中，您可以使用：</span><span class="sxs-lookup"><span data-stu-id="31c48-190">For example, in a project that has a reference to the Microsoft ActiveX Data Objects 2.8 Library COM object, you can use:</span></span>  
  
 [!code-vb[VbVbalrInterop#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#27)]  
  
## <a name="deploying-assemblies-that-expose-interop"></a><a name="vbconinteroperabilitymarshalinganchor12"></a> <span data-ttu-id="31c48-191">部署公開 Interop 的元件</span><span class="sxs-lookup"><span data-stu-id="31c48-191">Deploying Assemblies That Expose Interop</span></span>  

 <span data-ttu-id="31c48-192">部署公開 COM 介面的元件會帶來一些獨特的挑戰。</span><span class="sxs-lookup"><span data-stu-id="31c48-192">Deploying assemblies that expose COM interfaces presents some unique challenges.</span></span> <span data-ttu-id="31c48-193">例如，當不同的應用程式參考相同的 COM 元件時，就會發生潛在問題。</span><span class="sxs-lookup"><span data-stu-id="31c48-193">For example, a potential problem occurs when separate applications reference the same COM assembly.</span></span> <span data-ttu-id="31c48-194">當安裝新版本的元件，而另一個應用程式仍在使用舊版元件時，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="31c48-194">This situation is common when a new version of an assembly is installed and another application is still using the old version of the assembly.</span></span> <span data-ttu-id="31c48-195">如果您卸載共用 DLL 的元件，您可以不小心讓其他元件無法使用它。</span><span class="sxs-lookup"><span data-stu-id="31c48-195">If you uninstall an assembly that shares a DLL, you can unintentionally make it unavailable to the other assemblies.</span></span>  
  
 <span data-ttu-id="31c48-196">若要避免這個問題，您應該將共用的元件安裝到全域組件快取 (GAC) 並使用元件的 MergeModule。</span><span class="sxs-lookup"><span data-stu-id="31c48-196">To avoid this problem, you should install shared assemblies to the Global Assembly Cache (GAC) and use a MergeModule for the component.</span></span> <span data-ttu-id="31c48-197">如果您無法在 GAC 中安裝應用程式，則應該將它安裝到 CommonFilesFolder 的版本特定子目錄中。</span><span class="sxs-lookup"><span data-stu-id="31c48-197">If you cannot install the application in the GAC, it should be installed to CommonFilesFolder in a version-specific subdirectory.</span></span>  
  
 <span data-ttu-id="31c48-198">未共用的元件應該在具有呼叫應用程式的目錄中並存。</span><span class="sxs-lookup"><span data-stu-id="31c48-198">Assemblies that are not shared should be located side by side in the directory with the calling application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31c48-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31c48-199">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="31c48-200">COM Interop</span><span class="sxs-lookup"><span data-stu-id="31c48-200">COM Interop</span></span>](index.md)
- [<span data-ttu-id="31c48-201">Tlbimp.exe (類型程式庫匯入工具)</span><span class="sxs-lookup"><span data-stu-id="31c48-201">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="31c48-202">Tlbexp.exe (類型程式庫匯出工具)</span><span class="sxs-lookup"><span data-stu-id="31c48-202">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="31c48-203">逐步解說：實作 COM 物件的繼承</span><span class="sxs-lookup"><span data-stu-id="31c48-203">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="31c48-204">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="31c48-204">Inherits Statement</span></span>](../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="31c48-205">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="31c48-205">Global Assembly Cache</span></span>](../../../framework/app-domains/gac.md)
