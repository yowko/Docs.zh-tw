---
title: 以 F 開始使用 Azure 佇列儲存體#
description: Azure 佇列可在應用程式元件之間提供可靠的非同步傳訊。 雲端傳訊可讓您的應用程式元件獨立擴充。
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 0ab131647e37985d45073966ffc01b9a7f379e2f
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899291"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="5140f-104">以 F 開始使用 Azure 佇列儲存體\#</span><span class="sxs-lookup"><span data-stu-id="5140f-104">Get started with Azure Queue Storage using F\#</span></span>

<span data-ttu-id="5140f-105">Azure 佇列儲存體可提供應用程式元件之間的雲端通訊。</span><span class="sxs-lookup"><span data-stu-id="5140f-105">Azure Queue Storage provides cloud messaging between application components.</span></span> <span data-ttu-id="5140f-106">設計擴充性的應用程式時，會經常分離應用程式元件，以便進行個別擴充。</span><span class="sxs-lookup"><span data-stu-id="5140f-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="5140f-107">佇列儲存體可針對應用程式元件間的通訊，提供非同步傳訊，無論應用程式元件是在雲端、桌面、內部部署伺服器或行動裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="5140f-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="5140f-108">佇列儲存體也支援管理非同步工作並建置處理工作流程。</span><span class="sxs-lookup"><span data-stu-id="5140f-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="5140f-109">關於本教學課程</span><span class="sxs-lookup"><span data-stu-id="5140f-109">About this tutorial</span></span>

<span data-ttu-id="5140f-110">本教學課程說明如何使用 Azure 佇列儲存體來撰寫一些常見工作的 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="5140f-110">This tutorial shows how to write F# code for some common tasks using Azure Queue Storage.</span></span> <span data-ttu-id="5140f-111">涵蓋的工作包括建立和刪除佇列，以及新增、讀取和刪除佇列訊息。</span><span class="sxs-lookup"><span data-stu-id="5140f-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="5140f-112">如需佇列儲存體的概念總覽，請參閱 [佇列儲存體的 .net 指南](/azure/storage/storage-dotnet-how-to-use-queues)。</span><span class="sxs-lookup"><span data-stu-id="5140f-112">For a conceptual overview of queue storage, see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5140f-113">先決條件</span><span class="sxs-lookup"><span data-stu-id="5140f-113">Prerequisites</span></span>

<span data-ttu-id="5140f-114">若要使用本指南，您必須先 [建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。</span><span class="sxs-lookup"><span data-stu-id="5140f-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="5140f-115">您也需要此帳戶的儲存體存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="5140f-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="5140f-116">建立 F # 腳本並開始 F# 互動</span><span class="sxs-lookup"><span data-stu-id="5140f-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="5140f-117">本文中的範例可用於 F # 應用程式或 F # 腳本。</span><span class="sxs-lookup"><span data-stu-id="5140f-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="5140f-118">若要建立 F # 腳本，請 `.fsx` `queues.fsx` 在您的 f # 開發環境中建立副檔名為的檔案，例如。</span><span class="sxs-lookup"><span data-stu-id="5140f-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="5140f-119">接下來，使用 [套件管理員](package-management.md) （例如 [Paket](https://fsprojects.github.io/Paket/) 或 [NuGet](https://www.nuget.org/) ）， `WindowsAzure.Storage` `WindowsAzure.Storage.dll` 在您的腳本中使用指示詞安裝封裝和參考 `#r` 。</span><span class="sxs-lookup"><span data-stu-id="5140f-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="5140f-120">新增命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="5140f-120">Add namespace declarations</span></span>

<span data-ttu-id="5140f-121">在 `queues.fsx` 檔案頂端新增下列 `open` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="5140f-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="5140f-122">取得您的連接字串</span><span class="sxs-lookup"><span data-stu-id="5140f-122">Get your connection string</span></span>

<span data-ttu-id="5140f-123">在本教學課程中，您將需要 Azure 儲存體連接字串。</span><span class="sxs-lookup"><span data-stu-id="5140f-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="5140f-124">如需連接字串的詳細資訊，請參閱 [設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="5140f-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="5140f-125">在本教學課程中，您將在腳本中輸入連接字串，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5140f-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="5140f-126">不過，這不 **建議** 用於實際的專案。</span><span class="sxs-lookup"><span data-stu-id="5140f-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="5140f-127">儲存體帳戶金鑰很類似儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="5140f-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="5140f-128">請務必小心保護您的儲存體帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="5140f-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="5140f-129">請避免轉發給其他使用者、進行硬式編碼，或將它儲存在其他人可以存取的純文字檔案。</span><span class="sxs-lookup"><span data-stu-id="5140f-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="5140f-130">如果您認為金鑰可能已遭盜用，您可以使用 Azure 入口網站重新產生金鑰。</span><span class="sxs-lookup"><span data-stu-id="5140f-130">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="5140f-131">針對實際的應用程式，維護儲存體連接字串的最佳方式是在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="5140f-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="5140f-132">若要從設定檔提取連接字串，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5140f-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="5140f-133">是否使用 Azure Configuration Manager 可由您選擇。</span><span class="sxs-lookup"><span data-stu-id="5140f-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="5140f-134">您也可以使用 API，例如 .NET Framework 的型別 `ConfigurationManager` 。</span><span class="sxs-lookup"><span data-stu-id="5140f-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="5140f-135">解析連接字串</span><span class="sxs-lookup"><span data-stu-id="5140f-135">Parse the connection string</span></span>

<span data-ttu-id="5140f-136">若要剖析連接字串，請使用：</span><span class="sxs-lookup"><span data-stu-id="5140f-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="5140f-137">這會傳回 `CloudStorageAccount` 。</span><span class="sxs-lookup"><span data-stu-id="5140f-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="5140f-138">建立佇列服務用戶端</span><span class="sxs-lookup"><span data-stu-id="5140f-138">Create the Queue service client</span></span>

<span data-ttu-id="5140f-139">`CloudQueueClient`類別可讓您取出儲存在佇列儲存體中的佇列。</span><span class="sxs-lookup"><span data-stu-id="5140f-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="5140f-140">以下是建立服務用戶端的其中一種方式：</span><span class="sxs-lookup"><span data-stu-id="5140f-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="5140f-141">您現在可以開始撰寫程式碼，以讀取佇列儲存體的資料並將資料寫入其中。</span><span class="sxs-lookup"><span data-stu-id="5140f-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="5140f-142">建立佇列</span><span class="sxs-lookup"><span data-stu-id="5140f-142">Create a queue</span></span>

<span data-ttu-id="5140f-143">這個範例會示範如何建立佇列（如果尚未存在）：</span><span class="sxs-lookup"><span data-stu-id="5140f-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="5140f-144">將訊息插入佇列</span><span class="sxs-lookup"><span data-stu-id="5140f-144">Insert a message into a queue</span></span>

<span data-ttu-id="5140f-145">若要將訊息插入現有佇列，請先建立新的 `CloudQueueMessage` 。</span><span class="sxs-lookup"><span data-stu-id="5140f-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="5140f-146">接下來，呼叫 `AddMessage` 方法。</span><span class="sxs-lookup"><span data-stu-id="5140f-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="5140f-147">您 `CloudQueueMessage` 可以從字串 (採用 utf-8 格式) 或陣列來建立 `byte` ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5140f-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="5140f-148">查看下一個訊息</span><span class="sxs-lookup"><span data-stu-id="5140f-148">Peek at the next message</span></span>

<span data-ttu-id="5140f-149">您可以藉由呼叫方法，在佇列前面查看訊息，而不需要將它從佇列中移除 `PeekMessage` 。</span><span class="sxs-lookup"><span data-stu-id="5140f-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="5140f-150">取得下一個要處理的訊息</span><span class="sxs-lookup"><span data-stu-id="5140f-150">Get the next message for processing</span></span>

<span data-ttu-id="5140f-151">您可以藉由呼叫方法，在佇列前端取得訊息以進行處理 `GetMessage` 。</span><span class="sxs-lookup"><span data-stu-id="5140f-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="5140f-152">您稍後會使用來指示訊息的成功處理 `DeleteMessage` 。</span><span class="sxs-lookup"><span data-stu-id="5140f-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="5140f-153">變更佇列訊息的內容</span><span class="sxs-lookup"><span data-stu-id="5140f-153">Change the contents of a queued message</span></span>

<span data-ttu-id="5140f-154">您可以在佇列中就地變更已抓取訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="5140f-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="5140f-155">如果訊息代表工作作業，則您可以使用此功能來更新工作作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="5140f-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="5140f-156">下列程式碼將使用新的內容更新佇列訊息，並將可見度逾時設定延長 60 秒。</span><span class="sxs-lookup"><span data-stu-id="5140f-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="5140f-157">這可儲存與訊息相關的工作狀態，並提供用戶端多一分鐘的時間繼續處理訊息。</span><span class="sxs-lookup"><span data-stu-id="5140f-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="5140f-158">您可以使用此技巧來追蹤佇列訊息上的多步驟工作流程，如果因為硬體或軟體故障而導致某個處理步驟失敗，將無需從頭開始。</span><span class="sxs-lookup"><span data-stu-id="5140f-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="5140f-159">通常，您也會保留重試計數，如果訊息重試次數超過數次，您就會刪除它。</span><span class="sxs-lookup"><span data-stu-id="5140f-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="5140f-160">這麼做可防止每次處理時便觸發應用程式錯誤的訊息。</span><span class="sxs-lookup"><span data-stu-id="5140f-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="5140f-161">將下一個訊息清除佇列</span><span class="sxs-lookup"><span data-stu-id="5140f-161">De-queue the next message</span></span>

<span data-ttu-id="5140f-162">您的程式碼可以使用兩個步驟將訊息自佇列中清除佇列。</span><span class="sxs-lookup"><span data-stu-id="5140f-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="5140f-163">當您呼叫時 `GetMessage` ，會取得佇列中的下一則訊息。</span><span class="sxs-lookup"><span data-stu-id="5140f-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="5140f-164">從 `GetMessage` 傳回的訊息，對於從此佇列讀取訊息的任何其他程式碼而言，將會是不可見的。</span><span class="sxs-lookup"><span data-stu-id="5140f-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="5140f-165">依預設，此訊息會維持 30 秒的不可見狀態。</span><span class="sxs-lookup"><span data-stu-id="5140f-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="5140f-166">若要完成從佇列中移除訊息，您還必須呼叫 `DeleteMessage` 。</span><span class="sxs-lookup"><span data-stu-id="5140f-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="5140f-167">這個移除訊息的兩步驟程序可確保您的程式碼因為硬體或軟體故障而無法處理訊息時，另一個程式碼的執行個體可以取得相同訊息並再試一次。</span><span class="sxs-lookup"><span data-stu-id="5140f-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="5140f-168">您的程式碼會在 `DeleteMessage` 處理完訊息之後立即呼叫。</span><span class="sxs-lookup"><span data-stu-id="5140f-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="5140f-169">使用非同步工作流程搭配一般佇列儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="5140f-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="5140f-170">此範例示範如何使用非同步工作流程搭配一般佇列儲存體 Api。</span><span class="sxs-lookup"><span data-stu-id="5140f-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="5140f-171">其他將訊息移出佇列的選項</span><span class="sxs-lookup"><span data-stu-id="5140f-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="5140f-172">自訂從佇列中擷取訊息的方法有兩種。</span><span class="sxs-lookup"><span data-stu-id="5140f-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="5140f-173">首先，您可以取得一批訊息 (最多 32 個)。</span><span class="sxs-lookup"><span data-stu-id="5140f-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="5140f-174">其次，您可以設定較長或較短的可見度逾時，讓您的程式碼有較長或較短的時間可以完全處理每個訊息。</span><span class="sxs-lookup"><span data-stu-id="5140f-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="5140f-175">下列程式碼範例會使用 `GetMessages` 在一個呼叫中取得20個訊息，然後處理每個訊息。</span><span class="sxs-lookup"><span data-stu-id="5140f-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="5140f-176">它也會將可見度逾時設定為每個訊息五分鐘。</span><span class="sxs-lookup"><span data-stu-id="5140f-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="5140f-177">系統會為所有訊息同時開始5分鐘，因此在呼叫後經過5分鐘後 `GetMessages` ，任何尚未刪除的訊息都會重新顯示。</span><span class="sxs-lookup"><span data-stu-id="5140f-177">The 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages that have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="5140f-178">取得佇列長度</span><span class="sxs-lookup"><span data-stu-id="5140f-178">Get the queue length</span></span>

<span data-ttu-id="5140f-179">您可以取得佇列中的估計訊息數目。</span><span class="sxs-lookup"><span data-stu-id="5140f-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="5140f-180">`FetchAttributes`方法會要求佇列服務取出佇列屬性，包括訊息計數。</span><span class="sxs-lookup"><span data-stu-id="5140f-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="5140f-181">`ApproximateMessageCount`屬性會傳回方法所取出的最後一個值 `FetchAttributes` ，而不會呼叫佇列服務。</span><span class="sxs-lookup"><span data-stu-id="5140f-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="5140f-182">刪除佇列</span><span class="sxs-lookup"><span data-stu-id="5140f-182">Delete a queue</span></span>

<span data-ttu-id="5140f-183">若要刪除佇列及其內含的所有訊息，請 `Delete` 在佇列物件上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="5140f-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="5140f-184">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5140f-184">Next steps</span></span>

<span data-ttu-id="5140f-185">了解佇列儲存體的基礎概念之後，請參考下列連結以了解有關更複雜的儲存工作。</span><span class="sxs-lookup"><span data-stu-id="5140f-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="5140f-186">適用於 .NET 的 Azure 儲存體 API</span><span class="sxs-lookup"><span data-stu-id="5140f-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="5140f-187">Azure 儲存體型別提供者</span><span class="sxs-lookup"><span data-stu-id="5140f-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="5140f-188">Azure 儲存體團隊部落格</span><span class="sxs-lookup"><span data-stu-id="5140f-188">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="5140f-189">設定 Azure 儲存體連接字串</span><span class="sxs-lookup"><span data-stu-id="5140f-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="5140f-190">Azure 儲存體服務 REST API 參考</span><span class="sxs-lookup"><span data-stu-id="5140f-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
