---
title: 使用 F# 開始使用 Azure 佇列儲存體
description: Azure 佇列可在應用程式元件之間提供可靠且非同步訊息。 雲端通訊可讓您的應用程式元件獨立進行調整。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 65af98fb88e91d709eb0e35907cbc2dc097634d0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630478"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="37816-104">使用 F 開始使用 Azure 佇列儲存體\#</span><span class="sxs-lookup"><span data-stu-id="37816-104">Get started with Azure Queue storage using F\#</span></span>

<span data-ttu-id="37816-105">Azure 佇列儲存體提供應用程式元件之間的雲端通訊。</span><span class="sxs-lookup"><span data-stu-id="37816-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="37816-106">在設計調整的應用程式時, 應用程式元件通常會分離, 讓它們可以獨立調整。</span><span class="sxs-lookup"><span data-stu-id="37816-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="37816-107">佇列儲存體為應用程式元件之間的通訊提供非同步訊息, 不論它們是在雲端、桌面、內部部署伺服器或行動裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="37816-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="37816-108">佇列儲存體也支援管理非同步工作, 以及建立處理工作流程。</span><span class="sxs-lookup"><span data-stu-id="37816-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="37816-109">關於本教學課程</span><span class="sxs-lookup"><span data-stu-id="37816-109">About this tutorial</span></span>

<span data-ttu-id="37816-110">本教學課程說明如何使用F# Azure 佇列儲存體來撰寫一些常見工作的程式碼。</span><span class="sxs-lookup"><span data-stu-id="37816-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="37816-111">涵蓋的工作包括建立和刪除佇列, 以及新增、讀取和刪除佇列訊息。</span><span class="sxs-lookup"><span data-stu-id="37816-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="37816-112">如需佇列儲存體的概念總覽, 請參閱[佇列儲存體的 .net 指南](/azure/storage/storage-dotnet-how-to-use-queues)。</span><span class="sxs-lookup"><span data-stu-id="37816-112">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="37816-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="37816-113">Prerequisites</span></span>

<span data-ttu-id="37816-114">若要使用本指南, 您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。</span><span class="sxs-lookup"><span data-stu-id="37816-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="37816-115">您也需要此帳戶的儲存體存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="37816-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="37816-116">建立F#腳本並啟動F#互動式</span><span class="sxs-lookup"><span data-stu-id="37816-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="37816-117">本文中的範例可用於F#應用程式或F#腳本中。</span><span class="sxs-lookup"><span data-stu-id="37816-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="37816-118">若要建立F#腳本, 請在`.fsx` F#開發環境中建立`queues.fsx`副檔名為的檔案, 例如。</span><span class="sxs-lookup"><span data-stu-id="37816-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="37816-119">接下來, 使用[Paket](https://fsprojects.github.io/Paket/)或`WindowsAzure.Storage` [NuGet](https://www.nuget.org/)之類的[套件管理員](package-management.md), 在您的腳本中`WindowsAzure.Storage.dll`使用`#r`指示詞安裝封裝和參考。</span><span class="sxs-lookup"><span data-stu-id="37816-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="37816-120">新增命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="37816-120">Add namespace declarations</span></span>

<span data-ttu-id="37816-121">將下列`open`語句新增至檔案頂端`queues.fsx` :</span><span class="sxs-lookup"><span data-stu-id="37816-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="37816-122">取得您的連接字串</span><span class="sxs-lookup"><span data-stu-id="37816-122">Get your connection string</span></span>

<span data-ttu-id="37816-123">在本教學課程中, 您將需要 Azure 儲存體連接字串。</span><span class="sxs-lookup"><span data-stu-id="37816-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="37816-124">如需連接字串的詳細資訊, 請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="37816-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="37816-125">在本教學課程中, 您將在腳本中輸入連接字串, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="37816-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="37816-126">不過, 這**不建議**用於實際的專案。</span><span class="sxs-lookup"><span data-stu-id="37816-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="37816-127">您的儲存體帳戶金鑰類似于儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="37816-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="37816-128">請務必小心保護您的儲存體帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="37816-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="37816-129">請避免將它散發給其他使用者、進行硬式編碼, 或將它儲存在其他人可以存取的純文字檔案中。</span><span class="sxs-lookup"><span data-stu-id="37816-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="37816-130">如果您認為金鑰可能遭到入侵, 您可以使用 Azure 入口網站重新產生金鑰。</span><span class="sxs-lookup"><span data-stu-id="37816-130">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="37816-131">對於實際的應用程式而言, 維護儲存體連接字串的最佳方式是在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="37816-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="37816-132">若要從設定檔提取連接字串, 您可以執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="37816-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="37816-133">使用 Azure Configuration Manager 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="37816-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="37816-134">您也可以使用 API (例如 .NET Framework 的`ConfigurationManager`類型)。</span><span class="sxs-lookup"><span data-stu-id="37816-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="37816-135">剖析連接字串</span><span class="sxs-lookup"><span data-stu-id="37816-135">Parse the connection string</span></span>

<span data-ttu-id="37816-136">若要剖析連接字串, 請使用:</span><span class="sxs-lookup"><span data-stu-id="37816-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="37816-137">這會`CloudStorageAccount`傳回。</span><span class="sxs-lookup"><span data-stu-id="37816-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="37816-138">建立佇列服務用戶端</span><span class="sxs-lookup"><span data-stu-id="37816-138">Create the Queue service client</span></span>

<span data-ttu-id="37816-139">`CloudQueueClient`類別可讓您取出儲存在佇列儲存體中的佇列。</span><span class="sxs-lookup"><span data-stu-id="37816-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="37816-140">以下是建立服務用戶端的其中一種方式:</span><span class="sxs-lookup"><span data-stu-id="37816-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="37816-141">現在您已準備好撰寫程式碼, 以讀取資料並將資料寫入佇列儲存體。</span><span class="sxs-lookup"><span data-stu-id="37816-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="37816-142">建立佇列</span><span class="sxs-lookup"><span data-stu-id="37816-142">Create a queue</span></span>

<span data-ttu-id="37816-143">這個範例示範如何建立佇列 (如果尚未存在):</span><span class="sxs-lookup"><span data-stu-id="37816-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="37816-144">將訊息插入佇列中</span><span class="sxs-lookup"><span data-stu-id="37816-144">Insert a message into a queue</span></span>

<span data-ttu-id="37816-145">若要將訊息插入現有佇列, 請先建立新`CloudQueueMessage`的。</span><span class="sxs-lookup"><span data-stu-id="37816-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="37816-146">接下來, 呼叫`AddMessage`方法。</span><span class="sxs-lookup"><span data-stu-id="37816-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="37816-147">可以從字串 (採用 utf-8 格式) `byte`或陣列建立, 如下所示: `CloudQueueMessage`</span><span class="sxs-lookup"><span data-stu-id="37816-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="37816-148">查看下一個訊息</span><span class="sxs-lookup"><span data-stu-id="37816-148">Peek at the next message</span></span>

<span data-ttu-id="37816-149">藉由呼叫`PeekMessage`方法, 您可以在佇列前面查看訊息, 而不需將它從佇列中移除。</span><span class="sxs-lookup"><span data-stu-id="37816-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="37816-150">取得要處理的下一個訊息</span><span class="sxs-lookup"><span data-stu-id="37816-150">Get the next message for processing</span></span>

<span data-ttu-id="37816-151">您可以藉由呼叫`GetMessage`方法來抓取佇列前端的訊息, 以進行處理。</span><span class="sxs-lookup"><span data-stu-id="37816-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="37816-152">您稍後會使用`DeleteMessage`來指示訊息的處理成功。</span><span class="sxs-lookup"><span data-stu-id="37816-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="37816-153">變更佇列訊息的內容</span><span class="sxs-lookup"><span data-stu-id="37816-153">Change the contents of a queued message</span></span>

<span data-ttu-id="37816-154">您可以在佇列中就地變更抓取訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="37816-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="37816-155">如果訊息代表工作工作, 您可以使用這項功能來更新工作的狀態。</span><span class="sxs-lookup"><span data-stu-id="37816-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="37816-156">下列程式碼會以新的內容更新佇列訊息, 並將可見度 timeout 設定為延長另一個60秒。</span><span class="sxs-lookup"><span data-stu-id="37816-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="37816-157">這會儲存與訊息相關聯之工作的狀態, 並讓用戶端有另一分鐘的時間繼續處理訊息。</span><span class="sxs-lookup"><span data-stu-id="37816-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="37816-158">您可以使用這項技術來追蹤佇列訊息上的多步驟工作流程, 如果因硬體或軟體失敗而導致處理步驟失敗, 則不需要從頭開始。</span><span class="sxs-lookup"><span data-stu-id="37816-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="37816-159">一般來說, 您也會保留重試計數, 如果訊息重試超過數次, 您就會刪除它。</span><span class="sxs-lookup"><span data-stu-id="37816-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="37816-160">這會針對每次處理時觸發應用程式錯誤的訊息進行保護。</span><span class="sxs-lookup"><span data-stu-id="37816-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="37816-161">將下一個訊息取消佇列</span><span class="sxs-lookup"><span data-stu-id="37816-161">De-queue the next message</span></span>

<span data-ttu-id="37816-162">您的程式碼會以兩個步驟將訊息從佇列中取消佇列。</span><span class="sxs-lookup"><span data-stu-id="37816-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="37816-163">當您呼叫`GetMessage`時, 您會取得佇列中的下一個訊息。</span><span class="sxs-lookup"><span data-stu-id="37816-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="37816-164">從這個佇列讀取`GetMessage`訊息的任何其他程式碼, 都不會看到從傳回的訊息。</span><span class="sxs-lookup"><span data-stu-id="37816-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="37816-165">根據預設, 此訊息會在30秒內保持不可見。</span><span class="sxs-lookup"><span data-stu-id="37816-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="37816-166">若要完成從佇列中移除訊息的作業, 您也`DeleteMessage`必須呼叫。</span><span class="sxs-lookup"><span data-stu-id="37816-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="37816-167">這個移除訊息的兩步驟程式可確保您的程式碼因為硬體或軟體故障而無法處理訊息時, 另一個程式碼實例可以取得相同的訊息, 然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="37816-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="37816-168">您的程式`DeleteMessage`代碼會在處理完訊息之後立即呼叫。</span><span class="sxs-lookup"><span data-stu-id="37816-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="37816-169">使用具有一般佇列儲存體 Api 的非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="37816-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="37816-170">此範例示範如何搭配使用非同步工作流程與一般佇列儲存體 Api。</span><span class="sxs-lookup"><span data-stu-id="37816-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="37816-171">取消佇列訊息的其他選項</span><span class="sxs-lookup"><span data-stu-id="37816-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="37816-172">有兩種方式可以自訂佇列中的訊息抓取。</span><span class="sxs-lookup"><span data-stu-id="37816-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="37816-173">首先, 您可以取得一批訊息 (最多 32)。</span><span class="sxs-lookup"><span data-stu-id="37816-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="37816-174">第二, 您可以設定較長或較短的隱藏超時, 讓您的程式碼更多或更少的時間來完整處理每個訊息。</span><span class="sxs-lookup"><span data-stu-id="37816-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="37816-175">下列程式碼範例會`GetMessages`使用在一次呼叫中取得20個訊息, 然後處理每個訊息。</span><span class="sxs-lookup"><span data-stu-id="37816-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="37816-176">它也會將每個訊息的隱藏超時設定為5分鐘。</span><span class="sxs-lookup"><span data-stu-id="37816-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="37816-177">請注意, 所有訊息的5分鐘都會啟動一次, 因此在呼叫`GetMessages`之後的5分鐘過後, 任何尚未刪除的訊息都會再次顯示。</span><span class="sxs-lookup"><span data-stu-id="37816-177">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="37816-178">取得佇列長度</span><span class="sxs-lookup"><span data-stu-id="37816-178">Get the queue length</span></span>

<span data-ttu-id="37816-179">您可以取得佇列中的訊息數目估計。</span><span class="sxs-lookup"><span data-stu-id="37816-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="37816-180">`FetchAttributes`方法會要求佇列服務取得佇列屬性, 包括訊息計數。</span><span class="sxs-lookup"><span data-stu-id="37816-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="37816-181">屬性會傳回`FetchAttributes`方法所取得的最後一個值, 而不會呼叫佇列服務。 `ApproximateMessageCount`</span><span class="sxs-lookup"><span data-stu-id="37816-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="37816-182">刪除佇列</span><span class="sxs-lookup"><span data-stu-id="37816-182">Delete a queue</span></span>

<span data-ttu-id="37816-183">若要刪除佇列及其內含的所有訊息, 請在佇列物件`Delete`上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="37816-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="37816-184">後續步驟</span><span class="sxs-lookup"><span data-stu-id="37816-184">Next steps</span></span>

<span data-ttu-id="37816-185">既然您已瞭解佇列儲存體的基本概念, 請遵循下列連結以瞭解更複雜的儲存工作。</span><span class="sxs-lookup"><span data-stu-id="37816-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="37816-186">適用于 .NET 的 Azure 儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="37816-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="37816-187">Azure 儲存體型別提供者</span><span class="sxs-lookup"><span data-stu-id="37816-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="37816-188">Azure 儲存體小組的 Blog</span><span class="sxs-lookup"><span data-stu-id="37816-188">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="37816-189">設定 Azure 儲存體連接字串</span><span class="sxs-lookup"><span data-stu-id="37816-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="37816-190">Azure 儲存體 Services REST API 參考</span><span class="sxs-lookup"><span data-stu-id="37816-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
