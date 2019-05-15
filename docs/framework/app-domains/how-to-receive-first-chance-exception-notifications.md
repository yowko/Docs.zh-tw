---
title: 作法：接收第一個可能發生的例外狀況通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- first-chance exception notifications
- exceptions, first chance notifications
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3009bf9eb24c44cedc4021f3d09f1707ae2e40d8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593598"
---
# <a name="how-to-receive-first-chance-exception-notifications"></a><span data-ttu-id="a41cd-102">作法：接收第一個可能發生的例外狀況通知</span><span class="sxs-lookup"><span data-stu-id="a41cd-102">How to: Receive First-Chance Exception Notifications</span></span>
<span data-ttu-id="a41cd-103"><xref:System.AppDomain> 類別的 <xref:System.AppDomain.FirstChanceException> 事件可讓您在 Common Language Runtime 開始搜尋例外狀況處理常式之前，收到已擲回例外狀況的通知。</span><span class="sxs-lookup"><span data-stu-id="a41cd-103">The <xref:System.AppDomain.FirstChanceException> event of the <xref:System.AppDomain> class lets you receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>

 <span data-ttu-id="a41cd-104">這個事件是在應用程式定義域層級引發。</span><span class="sxs-lookup"><span data-stu-id="a41cd-104">The event is raised at the application domain level.</span></span> <span data-ttu-id="a41cd-105">執行的執行緒可以通過多個應用程式定義域；因此，在另一個應用程式定義域中無法處理某個應用程式定義域中未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a41cd-105">A thread of execution can pass through multiple application domains, so an exception that is unhandled in one application domain could be handled in another application domain.</span></span> <span data-ttu-id="a41cd-106">在應用程式定義域處理例外狀況之前，通知都會發生在每個已新增事件之處理常式的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="a41cd-106">The notification occurs in each application domain that has added a handler for the event, until an application domain handles the exception.</span></span>

 <span data-ttu-id="a41cd-107">本文中的程序和範例示範如何接收具有一個應用程式定義域的簡單程式中以及您所建立之應用程式定義域中第一個可能發生傳回型別的例外狀況通知。</span><span class="sxs-lookup"><span data-stu-id="a41cd-107">The procedures and examples in this article show how to receive first-chance exception notifications in a simple program that has one application domain, and in an application domain that you create.</span></span>

 <span data-ttu-id="a41cd-108">如需跨數個應用程式定義域的更複雜範例，請參閱 <xref:System.AppDomain.FirstChanceException> 事件的範例。</span><span class="sxs-lookup"><span data-stu-id="a41cd-108">For a more complex example that spans several application domains, see the example for the <xref:System.AppDomain.FirstChanceException> event.</span></span>

## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a><span data-ttu-id="a41cd-109">接收預設應用程式定義域中第一個可能發生傳回型別的例外狀況通知</span><span class="sxs-lookup"><span data-stu-id="a41cd-109">Receiving First-Chance Exception Notifications in the Default Application Domain</span></span>
 <span data-ttu-id="a41cd-110">在下列程序中，應用程式的進入點 (`Main()` 方法) 會在預設應用程式定義域中執行。</span><span class="sxs-lookup"><span data-stu-id="a41cd-110">In the following procedure, the entry point for the application, the `Main()` method, runs in the default application domain.</span></span>

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a><span data-ttu-id="a41cd-111">示範預設應用程式定義域中第一個可能發生傳回型別的例外狀況通知</span><span class="sxs-lookup"><span data-stu-id="a41cd-111">To demonstrate first-chance exception notifications in the default application domain</span></span>

1. <span data-ttu-id="a41cd-112">使用 Lambda 函式定義 <xref:System.AppDomain.FirstChanceException> 事件的事件處理常式，並將它附加至事件。</span><span class="sxs-lookup"><span data-stu-id="a41cd-112">Define an event handler for the <xref:System.AppDomain.FirstChanceException> event, using a lambda function, and attach it to the event.</span></span> <span data-ttu-id="a41cd-113">在此範例中，事件處理常式會列印已處理事件之應用程式定義域的名稱以及例外狀況的 <xref:System.Exception.Message%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a41cd-113">In this example, the event handler prints the name of the application domain where the event was handled and the exception's <xref:System.Exception.Message%2A> property.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]

2. <span data-ttu-id="a41cd-114">擲回並攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a41cd-114">Throw an exception and catch it.</span></span> <span data-ttu-id="a41cd-115">執行階段找到例外狀況處理常式之前，會引發 <xref:System.AppDomain.FirstChanceException> 事件，並顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="a41cd-115">Before the runtime locates the exception handler, the <xref:System.AppDomain.FirstChanceException> event is raised and displays a message.</span></span> <span data-ttu-id="a41cd-116">此訊息接在例外狀況處理常式所顯示的訊息後面。</span><span class="sxs-lookup"><span data-stu-id="a41cd-116">This message is followed by the message that is displayed by the exception handler.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]

3. <span data-ttu-id="a41cd-117">擲回但不會攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a41cd-117">Throw an exception, but do not catch it.</span></span> <span data-ttu-id="a41cd-118">執行階段尋找例外狀況處理常式之前，會引發 <xref:System.AppDomain.FirstChanceException> 事件，並顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="a41cd-118">Before the runtime looks for an exception handler, the <xref:System.AppDomain.FirstChanceException> event is raised and displays a message.</span></span> <span data-ttu-id="a41cd-119">沒有任何例外狀況處理常式，因此應用程式會終止。</span><span class="sxs-lookup"><span data-stu-id="a41cd-119">There is no exception handler, so the application terminates.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]

     <span data-ttu-id="a41cd-120">此程序的前三個步驟所示的程式碼會形成完整主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="a41cd-120">The code that is shown in the first three steps of this procedure forms a complete console application.</span></span> <span data-ttu-id="a41cd-121">應用程式的輸出會根據 .exe 檔案的名稱而不同，因為預設應用程式定義域的名稱包含 .exe 檔案的名稱和副檔名。</span><span class="sxs-lookup"><span data-stu-id="a41cd-121">The output from the application varies, depending on the name of the .exe file, because the name of the default application domain consists of the name and extension of the .exe file.</span></span> <span data-ttu-id="a41cd-122">請參閱下面以取得範例輸出。</span><span class="sxs-lookup"><span data-stu-id="a41cd-122">See the following for sample output.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]

## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a><span data-ttu-id="a41cd-123">接收另一個應用程式定義域中第一個可能發生傳回型別的例外狀況通知</span><span class="sxs-lookup"><span data-stu-id="a41cd-123">Receiving First-Chance Exception Notifications in Another Application Domain</span></span>
 <span data-ttu-id="a41cd-124">如果您的程式包含多個應用程式定義域，您可以選擇哪些應用程式網域會收到通知。</span><span class="sxs-lookup"><span data-stu-id="a41cd-124">If your program contains more than one application domain, you can choose which application domains receive notifications.</span></span>

#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a><span data-ttu-id="a41cd-125">接收您所建立之應用程式定義域中第一個可能發生傳回型別的例外狀況通知</span><span class="sxs-lookup"><span data-stu-id="a41cd-125">To receive first-chance exception notifications in an application domain that you create</span></span>

1. <span data-ttu-id="a41cd-126">定義 <xref:System.AppDomain.FirstChanceException> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a41cd-126">Define an event handler for the <xref:System.AppDomain.FirstChanceException> event.</span></span> <span data-ttu-id="a41cd-127">此範例使用 `static` 方法 (在 Visual Basic 中為 `Shared` 方法)，這個方法會列印已處理事件之應用程式定義域的名稱以及例外狀況的 <xref:System.Exception.Message%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a41cd-127">This example uses a `static` method (`Shared` method in Visual Basic) that prints the name of the application domain where the event was handled and the exception's <xref:System.Exception.Message%2A> property.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]

2. <span data-ttu-id="a41cd-128">建立應用程式定義域，並將事件處理常式新增至該應用程式定義域的 <xref:System.AppDomain.FirstChanceException> 事件。</span><span class="sxs-lookup"><span data-stu-id="a41cd-128">Create an application domain and add the event handler to the <xref:System.AppDomain.FirstChanceException> event for that application domain.</span></span> <span data-ttu-id="a41cd-129">在此範例中，應用程式定義域命名為 `AD1`。</span><span class="sxs-lookup"><span data-stu-id="a41cd-129">In this example, the application domain is named `AD1`.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]

     <span data-ttu-id="a41cd-130">您可以使用相同的方式在預設應用程式定義域中處理此事件。</span><span class="sxs-lookup"><span data-stu-id="a41cd-130">You can handle this event in the default application domain in the same way.</span></span> <span data-ttu-id="a41cd-131">在 `Main()` 中使用 `static` (在 Visual Basic 中為 `Shared`) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> 屬性，以取得預設應用程式定義域的參考。</span><span class="sxs-lookup"><span data-stu-id="a41cd-131">Use the `static` (`Shared` in Visual Basic) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property in `Main()` to get a reference to the default application domain.</span></span>

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a><span data-ttu-id="a41cd-132">示範應用程式定義域中第一個可能發生傳回型別的例外狀況通知</span><span class="sxs-lookup"><span data-stu-id="a41cd-132">To demonstrate first-chance exception notifications in the application domain</span></span>

1. <span data-ttu-id="a41cd-133">在您於上一個程序建立的應用程式定義域中建立 `Worker` 物件。</span><span class="sxs-lookup"><span data-stu-id="a41cd-133">Create a `Worker` object in the application domain that you created in the previous procedure.</span></span> <span data-ttu-id="a41cd-134">`Worker` 類別必須是公用，而且必須衍生自 <xref:System.MarshalByRefObject>，如本文結尾的完整範例所示。</span><span class="sxs-lookup"><span data-stu-id="a41cd-134">The `Worker` class must be public, and must derive from <xref:System.MarshalByRefObject>, as shown in the complete example at the end of this article.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]

2. <span data-ttu-id="a41cd-135">呼叫可擲回例外狀況之 `Worker` 物件的方法。</span><span class="sxs-lookup"><span data-stu-id="a41cd-135">Call a method of the `Worker` object that throws an exception.</span></span> <span data-ttu-id="a41cd-136">在此範例中，會呼叫 `Thrower` 方法兩次。</span><span class="sxs-lookup"><span data-stu-id="a41cd-136">In this example, the `Thrower` method is called twice.</span></span> <span data-ttu-id="a41cd-137">第一次，方法引數是 `true`，可讓方法攔截它自己的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a41cd-137">The first time, the method argument is `true`, which causes the method to catch its own exception.</span></span> <span data-ttu-id="a41cd-138">第二次，引數是 `false`，而 `Main()` 方法會攔截預設應用程式定義域中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a41cd-138">The second time, the argument is `false`, and the `Main()` method catches the exception in the default application domain.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]

3. <span data-ttu-id="a41cd-139">將程式碼放在 `Thrower` 方法中，以控制方法是否處理它自己的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a41cd-139">Place code in the `Thrower` method to control whether the method handles its own exception.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]

## <a name="example"></a><span data-ttu-id="a41cd-140">範例</span><span class="sxs-lookup"><span data-stu-id="a41cd-140">Example</span></span>
 <span data-ttu-id="a41cd-141">下列範例會建立名為 `AD1` 的應用程式定義域，並將事件處理常式新增至應用程式定義域的 <xref:System.AppDomain.FirstChanceException> 事件。</span><span class="sxs-lookup"><span data-stu-id="a41cd-141">The following example creates an application domain named `AD1` and adds an event handler to the application domain's <xref:System.AppDomain.FirstChanceException> event.</span></span> <span data-ttu-id="a41cd-142">此範例會在應用程式定義域中建立 `Worker` 類別的執行個體，並呼叫名為 `Thrower` 且擲回 <xref:System.ArgumentException> 的方法。</span><span class="sxs-lookup"><span data-stu-id="a41cd-142">The example creates an instance of the `Worker` class in the application domain, and calls a method named `Thrower` that throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="a41cd-143">根據其引數的值，方法會攔截例外狀況或無法處理它。</span><span class="sxs-lookup"><span data-stu-id="a41cd-143">Depending on the value of its argument, the method either catches the exception or fails to handle it.</span></span>

 <span data-ttu-id="a41cd-144">每次 `Thrower` 方法在 `AD1` 中擲回例外狀況時，都會在 `AD1` 中引發 <xref:System.AppDomain.FirstChanceException> 事件，而且事件處理常式會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="a41cd-144">Each time the `Thrower` method throws an exception in `AD1`, the <xref:System.AppDomain.FirstChanceException> event is raised in `AD1`, and the event handler displays a message.</span></span> <span data-ttu-id="a41cd-145">執行階段接著會尋找例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="a41cd-145">The runtime then looks for an exception handler.</span></span> <span data-ttu-id="a41cd-146">在第一個案例中，例外狀況處理常式位於 `AD1` 中。</span><span class="sxs-lookup"><span data-stu-id="a41cd-146">In the first case, the exception handler is found in `AD1`.</span></span> <span data-ttu-id="a41cd-147">在第二個案例中，此例外狀況未在 `AD1` 中處理，而是改為在預設應用程式定義域中攔截。</span><span class="sxs-lookup"><span data-stu-id="a41cd-147">In the second case, the exception is unhandled in `AD1`, and instead is caught in the default application domain.</span></span>

> [!NOTE]
>  <span data-ttu-id="a41cd-148">預設應用程式定義域的名稱與可執行檔的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="a41cd-148">The name of the default application domain is the same as the name of the executable.</span></span>

 <span data-ttu-id="a41cd-149">如果您將 <xref:System.AppDomain.FirstChanceException> 事件的處理常式新增至預設應用程式定義域，則會引發事件，並在預設應用程式定義域處理例外狀況之前處理事件。</span><span class="sxs-lookup"><span data-stu-id="a41cd-149">If you add a handler for the <xref:System.AppDomain.FirstChanceException> event to the default application domain, the event is raised and handled before the default application domain handles the exception.</span></span> <span data-ttu-id="a41cd-150">若要查看其運作，請在 `Main()` 開頭新增 C# 程式碼 `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (在 Visual Basic 中，為 `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`)。</span><span class="sxs-lookup"><span data-stu-id="a41cd-150">To see this, add the C# code `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (in Visual Basic, `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) at the beginning of `Main()`.</span></span>

 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]

## <a name="compiling-the-code"></a><span data-ttu-id="a41cd-151">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a41cd-151">Compiling the Code</span></span>

- <span data-ttu-id="a41cd-152">這個範例是命令列應用程式。</span><span class="sxs-lookup"><span data-stu-id="a41cd-152">This example is a command-line application.</span></span> <span data-ttu-id="a41cd-153">若要在 Visual Studio 中編譯和執行此程式碼，請在 `Main()` 結尾新增 C# 程式碼 `Console.ReadLine();` (在 Visual Basic 中，為 `Console.ReadLine()`)，防止在您讀取輸出之前關閉命令視窗。</span><span class="sxs-lookup"><span data-stu-id="a41cd-153">To compile and run this code in Visual Studio, add the C# code `Console.ReadLine();` (in Visual Basic, `Console.ReadLine()`) at the end of `Main()`, to prevent the command window from closing before you can read the output.</span></span>

## <a name="see-also"></a><span data-ttu-id="a41cd-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a41cd-154">See also</span></span>

- <xref:System.AppDomain.FirstChanceException>
