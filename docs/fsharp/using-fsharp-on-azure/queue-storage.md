---
title: "開始使用 Azure 佇列儲存體使用 F #"
description: "Azure 佇列提供可靠、 非同步應用程式元件之間的訊息。 雲端訊息可讓您獨立擴充的應用程式元件。"
keywords: "visual f #、 f #，功能性程式設計，.NET 中，.NET Core，Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 70dc554c-8f4d-42a7-8e2a-6438657d012a
ms.openlocfilehash: 50b2d69a1753add688aa14c3314a0ca2df9f03a4
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="3ead2-105">開始使用 Azure 佇列儲存體使用 F #</span><span class="sxs-lookup"><span data-stu-id="3ead2-105">Get started with Azure Queue storage using F#</span></span> #

<span data-ttu-id="3ead2-106">Azure 佇列儲存體提供雲端應用程式元件之間的傳訊。</span><span class="sxs-lookup"><span data-stu-id="3ead2-106">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="3ead2-107">在設計應用程式的小數位數時，應用程式元件通常分開處理，以便它們可以獨立擴充。</span><span class="sxs-lookup"><span data-stu-id="3ead2-107">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="3ead2-108">佇列儲存體提供非同步傳訊應用程式元件之間的通訊是否在雲端中，在桌面上，在內部部署伺服器上，或行動裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="3ead2-108">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="3ead2-109">佇列儲存體也支援管理非同步工作，以及建置程序工作流程。</span><span class="sxs-lookup"><span data-stu-id="3ead2-109">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="3ead2-110">關於本教學課程</span><span class="sxs-lookup"><span data-stu-id="3ead2-110">About this tutorial</span></span>

<span data-ttu-id="3ead2-111">本教學課程會示範如何撰寫使用 Azure 佇列儲存體的一些常見工作的 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ead2-111">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="3ead2-112">涵蓋的工作包括建立和刪除佇列並新增、 讀取和刪除佇列訊息。</span><span class="sxs-lookup"><span data-stu-id="3ead2-112">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="3ead2-113">佇列儲存體概念的概觀，請參閱[佇列儲存體的.NET 指南](/azure/storage/storage-dotnet-how-to-use-queues)。</span><span class="sxs-lookup"><span data-stu-id="3ead2-113">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3ead2-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="3ead2-114">Prerequisites</span></span>

<span data-ttu-id="3ead2-115">若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。</span><span class="sxs-lookup"><span data-stu-id="3ead2-115">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="3ead2-116">您還需要此帳戶的儲存體存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="3ead2-116">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="3ead2-117">建立 F # 指令碼，並開始 F # Interactive</span><span class="sxs-lookup"><span data-stu-id="3ead2-117">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="3ead2-118">這篇文章中的範例可以用於 F # 應用程式或 F # 指令碼。</span><span class="sxs-lookup"><span data-stu-id="3ead2-118">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="3ead2-119">若要建立 F # 指令碼，建立檔案之`.fsx`擴充功能，例如`queues.fsx`，F # 開發環境中。</span><span class="sxs-lookup"><span data-stu-id="3ead2-119">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="3ead2-120">接下來，使用[封裝管理員](package-management.md)例如[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`封裝和參考`WindowsAzure.Storage.dll`指令碼使用`#r`指示詞。</span><span class="sxs-lookup"><span data-stu-id="3ead2-120">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="3ead2-121">加入命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="3ead2-121">Add namespace declarations</span></span>

<span data-ttu-id="3ead2-122">加入下列`open`上方的陳述式`queues.fsx`檔案：</span><span class="sxs-lookup"><span data-stu-id="3ead2-122">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="3ead2-123">取得連接字串</span><span class="sxs-lookup"><span data-stu-id="3ead2-123">Get your connection string</span></span>

<span data-ttu-id="3ead2-124">此教學課程中，您將需要 Azure 儲存體連接字串。</span><span class="sxs-lookup"><span data-stu-id="3ead2-124">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="3ead2-125">如需連接字串的詳細資訊，請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="3ead2-125">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="3ead2-126">教學課程中，您會輸入您的連接字串中指令碼中，像這樣：</span><span class="sxs-lookup"><span data-stu-id="3ead2-126">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="3ead2-127">不過，這是**不建議**用於真實的專案。</span><span class="sxs-lookup"><span data-stu-id="3ead2-127">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="3ead2-128">儲存體帳戶金鑰是類似於儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="3ead2-128">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="3ead2-129">一律為保護您的儲存體帳戶金鑰，請小心。</span><span class="sxs-lookup"><span data-stu-id="3ead2-129">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="3ead2-130">避免將其散發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。</span><span class="sxs-lookup"><span data-stu-id="3ead2-130">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="3ead2-131">您可以重新產生您使用 Azure 入口網站，如果您認為可能已受到危害的金鑰。</span><span class="sxs-lookup"><span data-stu-id="3ead2-131">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="3ead2-132">用於真實的應用程式，以維護您的儲存體連接字串的最佳方式是在組態檔中。</span><span class="sxs-lookup"><span data-stu-id="3ead2-132">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="3ead2-133">若要從組態檔擷取連接字串，您可以：</span><span class="sxs-lookup"><span data-stu-id="3ead2-133">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="3ead2-134">使用 Azure 組態管理員是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="3ead2-134">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="3ead2-135">您也可以使用例如.NET Framework API`ConfigurationManager`型別。</span><span class="sxs-lookup"><span data-stu-id="3ead2-135">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="3ead2-136">剖析連接字串</span><span class="sxs-lookup"><span data-stu-id="3ead2-136">Parse the connection string</span></span>

<span data-ttu-id="3ead2-137">若要剖析的連接字串，使用：</span><span class="sxs-lookup"><span data-stu-id="3ead2-137">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="3ead2-138">這會傳回`CloudStorageAccount`。</span><span class="sxs-lookup"><span data-stu-id="3ead2-138">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="3ead2-139">建立佇列服務用戶端</span><span class="sxs-lookup"><span data-stu-id="3ead2-139">Create the Queue service client</span></span>

<span data-ttu-id="3ead2-140">`CloudQueueClient`類別可讓您擷取儲存在佇列儲存體中的佇列。</span><span class="sxs-lookup"><span data-stu-id="3ead2-140">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="3ead2-141">以下是如何建立服務用戶端：</span><span class="sxs-lookup"><span data-stu-id="3ead2-141">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="3ead2-142">現在您已準備好開始撰寫程式碼讀取資料，並將資料寫入至佇列儲存體。</span><span class="sxs-lookup"><span data-stu-id="3ead2-142">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="3ead2-143">建立佇列</span><span class="sxs-lookup"><span data-stu-id="3ead2-143">Create a queue</span></span>

<span data-ttu-id="3ead2-144">這個範例示範如何建立佇列，如果不存在：</span><span class="sxs-lookup"><span data-stu-id="3ead2-144">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="3ead2-145">將訊息插入佇列</span><span class="sxs-lookup"><span data-stu-id="3ead2-145">Insert a message into a queue</span></span>

<span data-ttu-id="3ead2-146">若要將訊息插入現有佇列，先建立新`CloudQueueMessage`。</span><span class="sxs-lookup"><span data-stu-id="3ead2-146">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="3ead2-147">接下來，呼叫`AddMessage`方法。</span><span class="sxs-lookup"><span data-stu-id="3ead2-147">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="3ead2-148">A`CloudQueueMessage`可以從其中建立格式的字串 （utf-8） 或`byte`陣列，像這樣：</span><span class="sxs-lookup"><span data-stu-id="3ead2-148">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="3ead2-149">查看下一個訊息</span><span class="sxs-lookup"><span data-stu-id="3ead2-149">Peek at the next message</span></span>

<span data-ttu-id="3ead2-150">而不移除它藉由呼叫從佇列查看訊息佇列中，前端`PeekMessage`方法。</span><span class="sxs-lookup"><span data-stu-id="3ead2-150">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="3ead2-151">取得下一個訊息處理</span><span class="sxs-lookup"><span data-stu-id="3ead2-151">Get the next message for processing</span></span>

<span data-ttu-id="3ead2-152">您可以藉由呼叫擷取的訊息在處理佇列的前端`GetMessage`方法。</span><span class="sxs-lookup"><span data-stu-id="3ead2-152">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="3ead2-153">您稍後使用來表示成功處理訊息`DeleteMessage`。</span><span class="sxs-lookup"><span data-stu-id="3ead2-153">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="3ead2-154">變更佇列的訊息的內容</span><span class="sxs-lookup"><span data-stu-id="3ead2-154">Change the contents of a queued message</span></span>

<span data-ttu-id="3ead2-155">您可以變更擷取的訊息就地佇列中的內容。</span><span class="sxs-lookup"><span data-stu-id="3ead2-155">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="3ead2-156">如果訊息代表的工作，您可以使用這項功能，來更新 「 工作 」 工作的狀態。</span><span class="sxs-lookup"><span data-stu-id="3ead2-156">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="3ead2-157">下列程式碼會更新新的內容，佇列訊息，並設定以擴充另一個 60 秒的可見度逾時。</span><span class="sxs-lookup"><span data-stu-id="3ead2-157">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="3ead2-158">這樣會節省與訊息相關聯的工作的狀態，並繼續處理訊息的另一個分鐘讓用戶端。</span><span class="sxs-lookup"><span data-stu-id="3ead2-158">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="3ead2-159">您可以使用這項技術，來追蹤訊息排入佇列，而不必從頭開始處理步驟失敗，因為硬體或軟體失敗時多步驟工作流程。</span><span class="sxs-lookup"><span data-stu-id="3ead2-159">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="3ead2-160">一般而言，您會保留重試計數，而且如果一些次數超過重試的訊息，則會刪除它。</span><span class="sxs-lookup"><span data-stu-id="3ead2-160">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="3ead2-161">這可防止每次處理時就會觸發應用程式錯誤的訊息。</span><span class="sxs-lookup"><span data-stu-id="3ead2-161">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="3ead2-162">清除佇列的下一個訊息</span><span class="sxs-lookup"><span data-stu-id="3ead2-162">De-queue the next message</span></span>

<span data-ttu-id="3ead2-163">您的程式碼會將佇列佇列將訊息從佇列中兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="3ead2-163">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="3ead2-164">當您呼叫`GetMessage`，您可以取得下一個訊息佇列中。</span><span class="sxs-lookup"><span data-stu-id="3ead2-164">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="3ead2-165">傳回訊息`GetMessage`變成看不到任何其他從此佇列讀取訊息的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ead2-165">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="3ead2-166">根據預設，此訊息會保持可見 30 秒。</span><span class="sxs-lookup"><span data-stu-id="3ead2-166">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="3ead2-167">若要完成從佇列移除訊息，您必須也呼叫`DeleteMessage`。</span><span class="sxs-lookup"><span data-stu-id="3ead2-167">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="3ead2-168">這兩個步驟的程序中移除訊息可確保，如果您的程式碼無法處理訊息，因為硬體或軟體失敗，另一個執行個體的程式碼可以取得相同的訊息並再試一次。</span><span class="sxs-lookup"><span data-stu-id="3ead2-168">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="3ead2-169">您的程式碼呼叫`DeleteMessage`處理訊息之後，以滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="3ead2-169">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="3ead2-170">使用一般佇列儲存體 Api 使用非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="3ead2-170">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="3ead2-171">這個範例會示範如何使用一般佇列儲存體 Api 使用非同步工作流程。</span><span class="sxs-lookup"><span data-stu-id="3ead2-171">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="3ead2-172">取消佇列訊息的其他選項</span><span class="sxs-lookup"><span data-stu-id="3ead2-172">Additional options for de-queuing messages</span></span>

<span data-ttu-id="3ead2-173">有兩種方式，您可以自訂從佇列擷取訊息。</span><span class="sxs-lookup"><span data-stu-id="3ead2-173">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="3ead2-174">首先，您可以取得一批訊息 （最多 32)。</span><span class="sxs-lookup"><span data-stu-id="3ead2-174">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="3ead2-175">接下來，您可以設定長或短過了隱藏逾時，可讓您的程式碼，更多或更少的時間來完整處理每個訊息。</span><span class="sxs-lookup"><span data-stu-id="3ead2-175">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="3ead2-176">下列程式碼範例使用`GetMessages`取得 20 中其中一個訊息呼叫然後再處理每個訊息。</span><span class="sxs-lookup"><span data-stu-id="3ead2-176">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="3ead2-177">它也會針對每個訊息的五分鐘設定過了隱藏逾時。</span><span class="sxs-lookup"><span data-stu-id="3ead2-177">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="3ead2-178">請注意，在 5 分鐘內啟動的所有訊息在相同的時間，因此之後 5 分鐘的時間已過呼叫`GetMessages`，任何已被刪除的訊息一次將變成可見。</span><span class="sxs-lookup"><span data-stu-id="3ead2-178">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="3ead2-179">取得佇列長度</span><span class="sxs-lookup"><span data-stu-id="3ead2-179">Get the queue length</span></span>

<span data-ttu-id="3ead2-180">您可以在佇列中取得估計的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="3ead2-180">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="3ead2-181">`FetchAttributes`方法會要求佇列服務擷取佇列的屬性，包括訊息計數。</span><span class="sxs-lookup"><span data-stu-id="3ead2-181">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="3ead2-182">`ApproximateMessageCount`屬性會傳回所擷取的最後一個值`FetchAttributes`方法，而不需要呼叫佇列服務。</span><span class="sxs-lookup"><span data-stu-id="3ead2-182">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="3ead2-183">刪除佇列</span><span class="sxs-lookup"><span data-stu-id="3ead2-183">Delete a queue</span></span>

<span data-ttu-id="3ead2-184">若要刪除佇列與在它所包含的所有訊息，請呼叫`Delete`上的佇列物件的方法。</span><span class="sxs-lookup"><span data-stu-id="3ead2-184">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="3ead2-185">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3ead2-185">Next steps</span></span>

<span data-ttu-id="3ead2-186">既然您已經學會佇列儲存體的基本概念，請遵循下列連結，以了解更複雜的儲存體工作。</span><span class="sxs-lookup"><span data-stu-id="3ead2-186">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="3ead2-187">適用於.NET 的 azure 儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="3ead2-187">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="3ead2-188">Azure 儲存體型別提供者</span><span class="sxs-lookup"><span data-stu-id="3ead2-188">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="3ead2-189">Azure 儲存體團隊部落格</span><span class="sxs-lookup"><span data-stu-id="3ead2-189">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="3ead2-190">設定 Azure 儲存體連接字串</span><span class="sxs-lookup"><span data-stu-id="3ead2-190">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="3ead2-191">Azure 儲存體服務 REST API 參考</span><span class="sxs-lookup"><span data-stu-id="3ead2-191">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
