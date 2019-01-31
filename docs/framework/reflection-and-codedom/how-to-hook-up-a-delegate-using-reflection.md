---
title: HOW TO：使用反映連結委派
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe90542d1ba106dd52e8995afab298b4b9f69899
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644387"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="09618-102">HOW TO：使用反映連結委派</span><span class="sxs-lookup"><span data-stu-id="09618-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="09618-103">當您使用反映來載入和執行組件時，無法使用 C# `+=` 運算子或 Visual Basic [AddHandler 陳述式](~/docs/visual-basic/language-reference/statements/addhandler-statement.md)這類語言功能來連結事件。</span><span class="sxs-lookup"><span data-stu-id="09618-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="09618-104">下列程序示範如何透過反映取得所有必要類型以將現有方法連結至事件，以及如何使用反映發出建立動態方法並將它連結至事件。</span><span class="sxs-lookup"><span data-stu-id="09618-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09618-105">如需連結事件處理委派的另一種方式，請參閱 <xref:System.Reflection.EventInfo> 類別之 <xref:System.Reflection.EventInfo.AddEventHandler%2A> 方法的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="09618-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="09618-106">使用反映連結委派</span><span class="sxs-lookup"><span data-stu-id="09618-106">To hook up a delegate using reflection</span></span>  
  
1.  <span data-ttu-id="09618-107">載入包含引發事件之類型的組件。</span><span class="sxs-lookup"><span data-stu-id="09618-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="09618-108">通常會使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法載入組件。</span><span class="sxs-lookup"><span data-stu-id="09618-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="09618-109">為了簡化此範例，會使用目前組件中的衍生形式，因此使用 <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> 方法來載入目前組件。</span><span class="sxs-lookup"><span data-stu-id="09618-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2.  <span data-ttu-id="09618-110">取得代表類型的 <xref:System.Type> 物件，並建立類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="09618-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="09618-111">因為表單具有預設建構函式，所以在下列程式碼中使用 <xref:System.Activator.CreateInstance%28System.Type%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="09618-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a default constructor.</span></span> <span data-ttu-id="09618-112">如果您所建立的類型沒有預設建構函式，則 <xref:System.Activator.CreateInstance%2A> 方法有數個其他多載可以使用。</span><span class="sxs-lookup"><span data-stu-id="09618-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a default constructor.</span></span> <span data-ttu-id="09618-113">新的執行個體會儲存為 <xref:System.Object> 類型，以維護不知道組件的故事</span><span class="sxs-lookup"><span data-stu-id="09618-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="09618-114">(反映可讓您取得組件中的類型，而不需要事先知道其名稱)。</span><span class="sxs-lookup"><span data-stu-id="09618-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3.  <span data-ttu-id="09618-115">取得代表事件的 <xref:System.Reflection.EventInfo> 物件，並使用 <xref:System.Reflection.EventInfo.EventHandlerType%2A> 屬性來取得用來處理事件之委派的類型。</span><span class="sxs-lookup"><span data-stu-id="09618-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="09618-116">在下列程式碼中，會取得 <xref:System.Windows.Forms.Control.Click> 事件的 <xref:System.Reflection.EventInfo>。</span><span class="sxs-lookup"><span data-stu-id="09618-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4.  <span data-ttu-id="09618-117">取得代表處理事件之方法的 <xref:System.Reflection.MethodInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="09618-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="09618-118">本主題後段的＜範例＞一節中的完整程式碼，包含了與 <xref:System.EventHandler> 委派的簽章相符的方法，此委派會處理 <xref:System.Windows.Forms.Control.Click> 事件，但是您也可以在執行階段產生動態方法。</span><span class="sxs-lookup"><span data-stu-id="09618-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="09618-119">如需詳細資訊，請參閱伴隨的程序中關於在執行階段使用動態方法產生事件處理常式的資訊。</span><span class="sxs-lookup"><span data-stu-id="09618-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5.  <span data-ttu-id="09618-120">使用 <xref:System.Delegate.CreateDelegate%2A> 方法，建立委派的執行個體。</span><span class="sxs-lookup"><span data-stu-id="09618-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="09618-121">此方法是 static (在 Visual Basic 中為 `Shared`)，因此必須提供委派類型。</span><span class="sxs-lookup"><span data-stu-id="09618-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="09618-122">建議使用接受 <xref:System.Reflection.MethodInfo> 之 <xref:System.Delegate.CreateDelegate%2A> 的多載。</span><span class="sxs-lookup"><span data-stu-id="09618-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6.  <span data-ttu-id="09618-123">取得 `add` 存取子方法，並叫用它來連結事件。</span><span class="sxs-lookup"><span data-stu-id="09618-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="09618-124">所有事件都有高階語言語法所隱藏的 `add` 存取子和 `remove` 存取子。</span><span class="sxs-lookup"><span data-stu-id="09618-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="09618-125">例如，C# 使用 `+=` 運算子來連結事件，Visual Basic 則使用 [AddHandler 陳述式](~/docs/visual-basic/language-reference/statements/addhandler-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="09618-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="09618-126">下列程式碼會取得 <xref:System.Windows.Forms.Control.Click> 事件的 `add` 存取子，以及透過晚期繫結叫用它，並傳入委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="09618-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="09618-127">引數必須傳遞為陣列。</span><span class="sxs-lookup"><span data-stu-id="09618-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7.  <span data-ttu-id="09618-128">測試事件。</span><span class="sxs-lookup"><span data-stu-id="09618-128">Test the event.</span></span> <span data-ttu-id="09618-129">下列程式碼顯示程式碼範例中所定義的表單。</span><span class="sxs-lookup"><span data-stu-id="09618-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="09618-130">按一下表單，會叫用事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="09618-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="09618-131">使用動態方法以在執行階段產生事件處理常式</span><span class="sxs-lookup"><span data-stu-id="09618-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1.  <span data-ttu-id="09618-132">使用輕量型動態方法和反映發出，可以在執行階段產生事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="09618-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="09618-133">若要建構事件處理常式，您需要委派的傳回型別和參數類型。</span><span class="sxs-lookup"><span data-stu-id="09618-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="09618-134">這些可以透過檢查委派的 `Invoke` 方法取得。</span><span class="sxs-lookup"><span data-stu-id="09618-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="09618-135">下列程式碼使用 `GetDelegateReturnType` 和 `GetDelegateParameterTypes` 方法來取得這項資訊。</span><span class="sxs-lookup"><span data-stu-id="09618-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="09618-136">這些方法的程式碼位於本主題稍後的＜範例＞一節中。</span><span class="sxs-lookup"><span data-stu-id="09618-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="09618-137">不需要命名 <xref:System.Reflection.Emit.DynamicMethod>，因此可以使用空字串。</span><span class="sxs-lookup"><span data-stu-id="09618-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="09618-138">在下列程式碼中，最後一個引數會建立動態方法與目前類型的關聯，並提供 `Example` 類別之所有公用和私用成員的委派存取權。</span><span class="sxs-lookup"><span data-stu-id="09618-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2.  <span data-ttu-id="09618-139">產生方法主體。</span><span class="sxs-lookup"><span data-stu-id="09618-139">Generate a method body.</span></span> <span data-ttu-id="09618-140">這個方法會載入字串、呼叫接受字串之 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> 方法的多載、從堆疊取出傳回值 (因為處理常式沒有傳回型別) 並傳回。</span><span class="sxs-lookup"><span data-stu-id="09618-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="09618-141">若要深入了解如何發出動態方法，請參閱[如何：定義和執行動態方法](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="09618-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3.  <span data-ttu-id="09618-142">呼叫 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> 方法，以完成動態方法。</span><span class="sxs-lookup"><span data-stu-id="09618-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="09618-143">使用 `add` 存取子，以將委派新增至事件的叫用清單。</span><span class="sxs-lookup"><span data-stu-id="09618-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4.  <span data-ttu-id="09618-144">測試事件。</span><span class="sxs-lookup"><span data-stu-id="09618-144">Test the event.</span></span> <span data-ttu-id="09618-145">下列程式碼會載入程式碼範例中所定義的表單。</span><span class="sxs-lookup"><span data-stu-id="09618-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="09618-146">按一下表單，會叫用預先定義的事件處理常式和發出的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="09618-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="09618-147">範例</span><span class="sxs-lookup"><span data-stu-id="09618-147">Example</span></span>  
 <span data-ttu-id="09618-148">下列程式碼範例示範如何使用反映以將現有方法連結至事件，同時示範如何使用 <xref:System.Reflection.Emit.DynamicMethod> 類別以在執行階段發出方法，並將它連結至事件。</span><span class="sxs-lookup"><span data-stu-id="09618-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="09618-149">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="09618-149">Compiling the Code</span></span>  
  
-   <span data-ttu-id="09618-150">此程式碼包含編譯所需的 C# `using` 陳述式 (Visual Basic 為 `Imports`)。</span><span class="sxs-lookup"><span data-stu-id="09618-150">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="09618-151">不需要任何其他組件參考，即可從命令列進行編譯。</span><span class="sxs-lookup"><span data-stu-id="09618-151">No additional assembly references are required for compiling from the command line.</span></span> <span data-ttu-id="09618-152">在 Visual Studio 中，您必須新增 System.Windows.Forms.dll 的參考，因為這個範例是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="09618-152">In Visual Studio you must add a reference to System.Windows.Forms.dll because this example is a console application.</span></span>  
  
-   <span data-ttu-id="09618-153">在命令列使用 csc.exe、vbc.exe 或 cl.exe 編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="09618-153">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="09618-154">若要編譯 Visual Studio 中的程式碼，請將它放在主控台應用程式專案範本。</span><span class="sxs-lookup"><span data-stu-id="09618-154">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09618-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09618-155">See also</span></span>
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="09618-156">如何：定義和執行動態方法</span><span class="sxs-lookup"><span data-stu-id="09618-156">How to: Define and Execute Dynamic Methods</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="09618-157">反映</span><span class="sxs-lookup"><span data-stu-id="09618-157">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
