---
title: 委派的一般模式
description: 了解在程式碼中使用委派，以避免元件之間強式結合的一般模式。
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: ea0e0b7af361b76c4b46b0a180e07b44c1fa07e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095694"
---
# <a name="common-patterns-for-delegates"></a><span data-ttu-id="4f1c2-103">委派的一般模式</span><span class="sxs-lookup"><span data-stu-id="4f1c2-103">Common Patterns for Delegates</span></span>

[<span data-ttu-id="4f1c2-104">上一步</span><span class="sxs-lookup"><span data-stu-id="4f1c2-104">Previous</span></span>](delegates-strongly-typed.md)

<span data-ttu-id="4f1c2-105">委派會提供一種機制，啟用與元件之間最小結合程度有關的軟體設計。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-105">Delegates provide a mechanism that enables software designs involving minimal coupling between components.</span></span>

<span data-ttu-id="4f1c2-106">這種設計的一個絕佳範例是 LINQ。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-106">One excellent example for this kind of design is LINQ.</span></span> <span data-ttu-id="4f1c2-107">LINQ 查詢運算式模式依賴其所有功能的委派。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-107">The LINQ Query Expression Pattern relies on delegates for all of its features.</span></span> <span data-ttu-id="4f1c2-108">請考量這個簡單範例：</span><span class="sxs-lookup"><span data-stu-id="4f1c2-108">Consider this simple example:</span></span>

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

<span data-ttu-id="4f1c2-109">這會篩選一系列的數字，只顯示小於值 10 的數字。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-109">This filters the sequence of numbers to only those less than the value 10.</span></span>
<span data-ttu-id="4f1c2-110">`Where` 方法會使用委派，來決定序列的哪些項目通過篩選。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-110">The `Where` method uses a delegate that determines which elements of a sequence pass the filter.</span></span> <span data-ttu-id="4f1c2-111">當您建立 LINQ 查詢時，會對此特定用途提供委派的實作。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-111">When you create a LINQ query, you supply the implementation of the delegate for this specific purpose.</span></span>

<span data-ttu-id="4f1c2-112">Where 方法的原型是︰</span><span class="sxs-lookup"><span data-stu-id="4f1c2-112">The prototype for the Where method is:</span></span>

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

<span data-ttu-id="4f1c2-113">這個範例會重複使用為 LINQ 一部分的所有方法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-113">This example is repeated with all the methods that are part of LINQ.</span></span> <span data-ttu-id="4f1c2-114">它們全都依賴管理特定查詢之程式碼的委派。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-114">They all rely on delegates for the code that manages the specific query.</span></span> <span data-ttu-id="4f1c2-115">此 API 設計模式是一種要學習和了解之功能強大的模式。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-115">This API design pattern is a very powerful one to learn and understand.</span></span>

<span data-ttu-id="4f1c2-116">這個簡單範例說明委派如何需要元件之間的極小結合程度。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-116">This simple example illustrates how delegates require very little coupling between components.</span></span> <span data-ttu-id="4f1c2-117">您不需要建立衍生自特定基底類別的類別。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-117">You don't need to create a class that derives from a particular base class.</span></span> <span data-ttu-id="4f1c2-118">您不需要實作特定介面。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-118">You don't need to implement a specific interface.</span></span>
<span data-ttu-id="4f1c2-119">唯一的需求是提供手邊工作的一個必要方法的實作。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-119">The only requirement is to provide the implementation of one method that is fundamental to the task at hand.</span></span>

## <a name="building-your-own-components-with-delegates"></a><span data-ttu-id="4f1c2-120">使用委派建置自己的元件</span><span class="sxs-lookup"><span data-stu-id="4f1c2-120">Building Your Own Components with Delegates</span></span>

<span data-ttu-id="4f1c2-121">讓我們使用依賴委派的設計來建立元件，以建置該範例。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-121">Let's build on that example by creating a component using a design that relies on delegates.</span></span>

<span data-ttu-id="4f1c2-122">讓我們定義可以用於大型系統中記錄檔訊息的元件。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-122">Let's define a component that could be used for log messages in a large system.</span></span> <span data-ttu-id="4f1c2-123">程式庫元件可以用於許多不同環境的多個不同平台上。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-123">The library components could be used in many different environments, on multiple different platforms.</span></span> <span data-ttu-id="4f1c2-124">在管理記錄檔的元件中有許多一般功能。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-124">There are a lot of common features in the component that manages the logs.</span></span> <span data-ttu-id="4f1c2-125">它必須接受系統中任何元件的訊息。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-125">It will need to accept messages from any component in the system.</span></span> <span data-ttu-id="4f1c2-126">這些訊息將會有核心元件可管理的不同優先順序。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-126">Those messages will have different priorities, which the core component can manage.</span></span> <span data-ttu-id="4f1c2-127">訊息的最終保存格式應該會有時間戳記。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-127">The messages should have timestamps in their final archived form.</span></span> <span data-ttu-id="4f1c2-128">如需更進階的案例，您可以依來源元件來篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-128">For more advanced scenarios, you could filter messages by the source component.</span></span>

<span data-ttu-id="4f1c2-129">功能有一個部分會經常變更︰即寫入訊息。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-129">There is one aspect of the feature that will change often: where messages are written.</span></span> <span data-ttu-id="4f1c2-130">在某些環境中，它們可能會寫入至錯誤主控台。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-130">In some environments, they may be written to the error console.</span></span> <span data-ttu-id="4f1c2-131">在其他環境中，則會寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-131">In others, a file.</span></span> <span data-ttu-id="4f1c2-132">其他可能性包括資料庫儲存空間、OS 事件記錄檔或其他文件儲存空間。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-132">Other possibilities include database storage, OS event logs, or other document storage.</span></span>

<span data-ttu-id="4f1c2-133">也可以在不同案例中使用輸出的組合。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-133">There are also combinations of output that might be used in different scenarios.</span></span> <span data-ttu-id="4f1c2-134">您可能會想要將訊息寫入至主控台和檔案。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-134">You may want to write messages to the console and to a file.</span></span>

<span data-ttu-id="4f1c2-135">以委派為基礎的設計將提供相當大的彈性，並輕鬆地支援可在未來新增的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-135">A design based on delegates will provide a great deal of flexibility, and make it easy to support storage mechanisms that may be added in the future.</span></span>

<span data-ttu-id="4f1c2-136">透過這種設計，主要記錄元件可以是非虛擬，即使是密封類別也是一樣。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-136">Under this design, the primary log component can be a non-virtual, even sealed class.</span></span> <span data-ttu-id="4f1c2-137">您可以插入任何一組的委派，以將訊息寫入至不同的儲存媒體。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-137">You can plug in any set of delegates to write the messages to different storage media.</span></span> <span data-ttu-id="4f1c2-138">多點傳送委派的內建支援可讓您更輕鬆地支援必須將訊息寫入至多個位置 (檔案和主控台) 的案例。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-138">The built in support for multicast delegates makes it easy to support scenarios where messages must be written to multiple locations (a file, and a console).</span></span>

## <a name="a-first-implementation"></a><span data-ttu-id="4f1c2-139">第一個實作</span><span class="sxs-lookup"><span data-stu-id="4f1c2-139">A First Implementation</span></span>

<span data-ttu-id="4f1c2-140">讓我們開始︰初始實作將接受新訊息，並使用任何附加的委派來寫入它們。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-140">Let's start small: the initial implementation will accept new messages, and write them using any attached delegate.</span></span> <span data-ttu-id="4f1c2-141">您可以開始使用一個將訊息寫入至主控台的委派。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-141">You can start with one delegate that writes messages to the console.</span></span>

[!code-csharp[LoggerImplementation](../../samples/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

<span data-ttu-id="4f1c2-142">上述靜態類別是可運作的最簡單事項。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-142">The static class above is the simplest thing that can work.</span></span> <span data-ttu-id="4f1c2-143">我們需要撰寫將訊息寫入主控台之方法的單一實作︰</span><span class="sxs-lookup"><span data-stu-id="4f1c2-143">We need to write the single implementation for the method that writes messages to the console:</span></span> 

[!code-csharp[LogToConsole](../../samples/csharp/delegates-and-events/Program.cs#LogToConsole "A Console logger.")]

<span data-ttu-id="4f1c2-144">最後，您必須連結委派，方法是將它附加到記錄器中所宣告的 WriteMessage 委派︰</span><span class="sxs-lookup"><span data-stu-id="4f1c2-144">Finally, you need to hook up the delegate by attaching it to the WriteMessage delegate declared in the logger:</span></span>

[!code-csharp[ConnectDelegate](../../samples/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a><span data-ttu-id="4f1c2-145">做法</span><span class="sxs-lookup"><span data-stu-id="4f1c2-145">Practices</span></span>

<span data-ttu-id="4f1c2-146">我們的範例到目前為止都相當簡單，但它仍會示範與委派有關之設計的一些重要指導方針。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-146">Our sample so far is fairly simple, but it still demonstrates some of the important guidelines for designs involving delegates.</span></span>

<span data-ttu-id="4f1c2-147">使用核心架構中所定義的委派類型，可讓使用者輕鬆地使用委派。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-147">Using the delegate types defined in the Core Framework makes it easier for users to work with the delegates.</span></span> <span data-ttu-id="4f1c2-148">您不需要定義新類型，而且使用您程式庫的開發人員不需要學習新的特殊委派類型。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-148">You don't need to define new types, and developers using your library do not need to learn new, specialized delegate types.</span></span>

<span data-ttu-id="4f1c2-149">所使用的介面將會盡可能簡化並具有彈性：若要建立新的輸出記錄器，您必須建立一個方法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-149">The interfaces used are as minimal and as flexible as possible: To create a new output logger, you must create one method.</span></span> <span data-ttu-id="4f1c2-150">該方法可能是靜態方法或執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-150">That method may be a static method, or an instance method.</span></span> <span data-ttu-id="4f1c2-151">它可能會任何存取權。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-151">It may have any access.</span></span>

## <a name="formatting-output"></a><span data-ttu-id="4f1c2-152">Formatting Output</span><span class="sxs-lookup"><span data-stu-id="4f1c2-152">Formatting Output</span></span>

<span data-ttu-id="4f1c2-153">讓我們使第一版更為強固，然後開始建立其他記錄機制。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-153">Let's make this first version a bit more robust, and then start creating other logging mechanisms.</span></span>

<span data-ttu-id="4f1c2-154">接下來，讓我們將幾個引數新增至 `LogMessage()` 方法，讓您的記錄類別建立更結構化的訊息︰</span><span class="sxs-lookup"><span data-stu-id="4f1c2-154">Next, let's add a few arguments to the `LogMessage()` method so that your log class creates more structured messages:</span></span>

[!code-csharp[Severity](../../samples/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

<span data-ttu-id="4f1c2-155">接下來，讓我們使用該 `Severity` 引數，來篩選傳送到記錄檔輸出的訊息。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-155">Next, let's make use of that `Severity` argument to filter the messages that are sent to the log's output.</span></span> 

[!code-csharp[FinalLogger](../../samples/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a><span data-ttu-id="4f1c2-156">做法</span><span class="sxs-lookup"><span data-stu-id="4f1c2-156">Practices</span></span>

<span data-ttu-id="4f1c2-157">您已將新功能新增至記錄基礎結構。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-157">You've added new features to the logging infrastructure.</span></span> <span data-ttu-id="4f1c2-158">因為記錄器元件極為鬆散結合到任何輸出機制，所以可以新增這些新功能，而不會影響任何實作記錄器委派的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-158">Because the logger component is very loosely coupled to any output mechanism, these new features can be added with no impact on any of the code implementing the logger delegate.</span></span>

<span data-ttu-id="4f1c2-159">當您持續建置這項作業時，會看到更多範例來說明鬆散結合如何啟用更大的彈性來更新網站的各部分，而不需要對其他位置進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-159">As you keep building this, you'll see more examples of how this loose coupling enables greater flexibility in updating parts of the site without any changes to other locations.</span></span> <span data-ttu-id="4f1c2-160">事實上，在較大的應用程式中，記錄器輸出類別可能位於不同的組件中，甚至不需要重新建置。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-160">In fact, in a larger application, the logger output classes might be in a different assembly, and not even need to be rebuilt.</span></span>

## <a name="building-a-second-output-engine"></a><span data-ttu-id="4f1c2-161">建置第二個輸出引擎</span><span class="sxs-lookup"><span data-stu-id="4f1c2-161">Building a Second Output Engine</span></span>

<span data-ttu-id="4f1c2-162">也會提供記錄元件。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-162">The Log component is coming along well.</span></span> <span data-ttu-id="4f1c2-163">讓我們新增將訊息記錄到檔案的另一個輸出引擎。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-163">Let's add one more output engine that logs messages to a file.</span></span> <span data-ttu-id="4f1c2-164">這會更為牽涉到輸出引擎。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-164">This will be a slightly more involved output engine.</span></span> <span data-ttu-id="4f1c2-165">它將是封裝檔案作業的類別，並確保一律在每次寫入後關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-165">It will be a class that encapsulates the file operations, and ensures that the file is always closed after each write.</span></span> <span data-ttu-id="4f1c2-166">這確保在產生每個訊息之後，將所有資料都排清至磁碟。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-166">That ensures that all the data is flushed to disk after each message is generated.</span></span>

<span data-ttu-id="4f1c2-167">以下是檔案型記錄器︰</span><span class="sxs-lookup"><span data-stu-id="4f1c2-167">Here is that file based logger:</span></span>

[!code-csharp[FileLogger](../../samples/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]

<span data-ttu-id="4f1c2-168">建立這個類別之後，即可將它具現化，而且它會將其 LogMessage 方法附加至記錄器元件︰</span><span class="sxs-lookup"><span data-stu-id="4f1c2-168">Once you've created this class, you can instantiate it and it attaches its LogMessage method to the Logger component:</span></span>

[!code-csharp[FileLogger](../../samples/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

<span data-ttu-id="4f1c2-169">這兩者不互斥。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-169">These two are not mutually exclusive.</span></span> <span data-ttu-id="4f1c2-170">您可以連接這兩種記錄方法，並將訊息產生到主控台和檔案︰</span><span class="sxs-lookup"><span data-stu-id="4f1c2-170">You could attach both log methods and generate messages to the console and a file:</span></span>

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

<span data-ttu-id="4f1c2-171">稍後，即使在相同的應用程式中，您還是可以移除其中一個委派，而且系統不會有任何其他問題︰</span><span class="sxs-lookup"><span data-stu-id="4f1c2-171">Later, even in the same application, you can remove one of the delegates without any other issues to the system:</span></span>

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a><span data-ttu-id="4f1c2-172">做法</span><span class="sxs-lookup"><span data-stu-id="4f1c2-172">Practices</span></span>

<span data-ttu-id="4f1c2-173">現在，您已經新增記錄子系統的第二個輸出處理常式。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-173">Now, you've added a second output handler for the logging sub-system.</span></span>
<span data-ttu-id="4f1c2-174">這個需要更多的基礎結構，才能正確支援檔案系統。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-174">This one needs a bit more infrastructure to correctly support the file system.</span></span> <span data-ttu-id="4f1c2-175">委派是執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-175">The delegate is an instance method.</span></span> <span data-ttu-id="4f1c2-176">它也是私用方法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-176">It's also a private method.</span></span>
<span data-ttu-id="4f1c2-177">因為委派基礎結構都可以連接委派，所以不需要更大的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-177">There's no need for greater accessibility because the delegate infrastructure can connect the delegates.</span></span>

<span data-ttu-id="4f1c2-178">其次，委派設計會啟用多個輸出方法，而不需要任何額外程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-178">Second, the delegate-based design enables multiple output methods without any extra code.</span></span> <span data-ttu-id="4f1c2-179">您不需要建置任何額外基礎結構，即可支援多個輸出方法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-179">You don't need to build any additional infrastructure to support multiple output methods.</span></span> <span data-ttu-id="4f1c2-180">它們只會變成引動過程清單上的另一種方法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-180">They simply become another method on the invocation list.</span></span>

<span data-ttu-id="4f1c2-181">請特別注意記錄輸出方法之檔案中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-181">Pay special attention to the code in the file logging output method.</span></span> <span data-ttu-id="4f1c2-182">對它編寫程式碼，確保不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-182">It is coded to ensure that it does not throw any exceptions.</span></span> <span data-ttu-id="4f1c2-183">雖然這不一定絕對需要，但通常是不錯的做法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-183">While this isn't always strictly necessary, it's often a good practice.</span></span> <span data-ttu-id="4f1c2-184">如果其中一個委派方法擲回例外狀況，則不會叫用引動過程上的其餘委派。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-184">If either of the delegate methods throws an exception, the remaining delegates that are on the invocation won't be invoked.</span></span>

<span data-ttu-id="4f1c2-185">最後請注意，檔案記錄器必須開啟和關閉每個記錄檔訊息上的檔案，以管理其資源。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-185">As a last note, the file logger must manage its resources by opening and closing the file on each log message.</span></span> <span data-ttu-id="4f1c2-186">您可以選擇讓檔案保持開啟，並實作 IDisposable 以在完成時關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-186">You could choose to keep the file open and implement IDisposable to close the file when you are completed.</span></span>
<span data-ttu-id="4f1c2-187">任一個方法都會有其優缺點。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-187">Either method has its advantages and disadvantages.</span></span> <span data-ttu-id="4f1c2-188">兩者都會建立類別之間更多的結合程度。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-188">Both do create a bit more coupling between the classes.</span></span>

<span data-ttu-id="4f1c2-189">不需要更新記錄器類別中的程式碼，即可支援任一案例。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-189">None of the code in the Logger class would need to be updated in order to support either scenario.</span></span>

## <a name="handling-null-delegates"></a><span data-ttu-id="4f1c2-190">處理 Null 委派</span><span class="sxs-lookup"><span data-stu-id="4f1c2-190">Handling Null Delegates</span></span>

<span data-ttu-id="4f1c2-191">最後，讓我們更新 LogMessage 方法，以在未選取輸出機制時，在大部分情況下都更為強固。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-191">Finally, let's update the LogMessage method so that it is robust for those cases when no output mechanism is selected.</span></span> <span data-ttu-id="4f1c2-192">目前實作將會在 `WriteMessage` 委派未附加引動過程清單時擲回 `NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-192">The current implementation will throw a `NullReferenceException` when the `WriteMessage` delegate does not have an invocation list attached.</span></span>
<span data-ttu-id="4f1c2-193">您可能會偏好的設計是在未附加任何方法時，以無訊息模式繼續進行。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-193">You may prefer a design that silently continues when no methods have been attached.</span></span> <span data-ttu-id="4f1c2-194">搭配使用 Null 條件運算子與 `Delegate.Invoke()` 方法，這個作業即容易達成：</span><span class="sxs-lookup"><span data-stu-id="4f1c2-194">This is easy using the null conditional operator, combined with the `Delegate.Invoke()` method:</span></span>

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

<span data-ttu-id="4f1c2-195">左運算元 (在此情況下為 `WriteMessage`) 為 Null 時，Null 條件運算子 (`?.`) 會短路，這表示不會嘗試記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-195">The null conditional operator (`?.`) short-circuits when the left operand (`WriteMessage` in this case) is null, which means no attempt is made to log a message.</span></span>

<span data-ttu-id="4f1c2-196">您找不到 `System.Delegate` 或 `System.MulticastDelegate` 的文件中所列的 `Invoke()` 方法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-196">You won't find the `Invoke()` method listed in the documentation for `System.Delegate` or `System.MulticastDelegate`.</span></span> <span data-ttu-id="4f1c2-197">編譯器會針對任何宣告的委派類型產生類型安全 `Invoke` 方法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-197">The compiler generates a type safe `Invoke` method for any delegate type declared.</span></span> <span data-ttu-id="4f1c2-198">在此範例中，這表示 `Invoke` 接受單一 `string` 引數，且具有 void 傳回型別。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-198">In this example, that means `Invoke` takes a single `string` argument, and has a void return type.</span></span>

## <a name="summary-of-practices"></a><span data-ttu-id="4f1c2-199">做法摘要</span><span class="sxs-lookup"><span data-stu-id="4f1c2-199">Summary of Practices</span></span>

<span data-ttu-id="4f1c2-200">您已了解可以使用其他寫入器和其他功能來擴充記錄元件的開頭。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-200">You've seen the beginnings of a log component that could be expanded with other writers, and other features.</span></span> <span data-ttu-id="4f1c2-201">在設計中使用委派，這些不同元件的結合十分鬆散。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-201">By using delegates in the design these different components are very loosely coupled.</span></span> <span data-ttu-id="4f1c2-202">這提供幾項優點。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-202">This provides several advantages.</span></span> <span data-ttu-id="4f1c2-203">它很容易建立新的輸出機制，並將它們附加至系統。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-203">It's very easy to create new output mechanisms and attach them to the system.</span></span> <span data-ttu-id="4f1c2-204">這些其他機制只需要一個方法︰寫入記錄訊息的方法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-204">These other mechanisms only need one method: the method that writes the log message.</span></span> <span data-ttu-id="4f1c2-205">新增功能時，這是很有彈性的設計。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-205">It's a design that is very resilient when new features are added.</span></span> <span data-ttu-id="4f1c2-206">任何寫入器所需的合約都是實作一個方法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-206">The contract required for any writer is to implement one method.</span></span> <span data-ttu-id="4f1c2-207">該方法可以是靜態或執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-207">That method could be a static or instance method.</span></span> <span data-ttu-id="4f1c2-208">它可以是公用、私用或任何其他合法存取。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-208">It could be public, private, or any other legal access.</span></span>

<span data-ttu-id="4f1c2-209">記錄器類別可以進行任意數目的增強或變更，而不需要中斷變更。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-209">The Logger class can make any number of enhancements or changes without introducing breaking changes.</span></span> <span data-ttu-id="4f1c2-210">與任何類別一樣，修改公用 API 會有中斷變更的風險。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-210">Like any class, you cannot modify the public API without the risk of breaking changes.</span></span> <span data-ttu-id="4f1c2-211">但是，因為記錄器與任何輸出引擎之間的結合程度只能透過委派，所以不會包含其他類型 (例如介面或基底類別)。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-211">But, because the coupling between the logger and any output engines is only through the delegate, no other types (like interfaces or base classes) are involved.</span></span> <span data-ttu-id="4f1c2-212">結合程度越小越好。</span><span class="sxs-lookup"><span data-stu-id="4f1c2-212">The coupling is as small as possible.</span></span>

[<span data-ttu-id="4f1c2-213">下一步</span><span class="sxs-lookup"><span data-stu-id="4f1c2-213">Next</span></span>](events-overview.md)
