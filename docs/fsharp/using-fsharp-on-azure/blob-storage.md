---
title: 使用 F# 開始使用 Azure Blob 儲存體
description: 使用 Azure Blob 儲存體, 將非結構化資料儲存在雲端。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: c8b42339ff1d76f262e956b5e34cc598e0fc855d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630504"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="68bf7-103">開始使用 F 來使用 Azure Blob 儲存體\#</span><span class="sxs-lookup"><span data-stu-id="68bf7-103">Get started with Azure Blob storage using F\#</span></span>

<span data-ttu-id="68bf7-104">Azure Blob 儲存體是可將非結構化的資料儲存在雲端作為物件/Blob 的服務。</span><span class="sxs-lookup"><span data-stu-id="68bf7-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="68bf7-105">Blob 儲存體可以儲存任何類型的文字或二進位資料，例如文件、媒體檔案或應用程式安裝程式。</span><span class="sxs-lookup"><span data-stu-id="68bf7-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="68bf7-106">Blob 儲存體也稱為物件儲存體。</span><span class="sxs-lookup"><span data-stu-id="68bf7-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="68bf7-107">本文說明如何使用 Blob 儲存體執行一般工作。</span><span class="sxs-lookup"><span data-stu-id="68bf7-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="68bf7-108">這些範例是使用F#適用于 .net 的 Azure 儲存體用戶端程式庫來撰寫。</span><span class="sxs-lookup"><span data-stu-id="68bf7-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="68bf7-109">涵蓋的工作包括如何上傳、列出、下載和刪除 blob。</span><span class="sxs-lookup"><span data-stu-id="68bf7-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="68bf7-110">如需 blob 儲存體的概念總覽, 請參閱[blob 儲存體的 .net 指南](/azure/storage/storage-dotnet-how-to-use-blobs)。</span><span class="sxs-lookup"><span data-stu-id="68bf7-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="68bf7-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="68bf7-111">Prerequisites</span></span>

<span data-ttu-id="68bf7-112">若要使用本指南, 您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。</span><span class="sxs-lookup"><span data-stu-id="68bf7-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="68bf7-113">您也需要此帳戶的儲存體存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="68bf7-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="68bf7-114">建立F#腳本並啟動F#互動式</span><span class="sxs-lookup"><span data-stu-id="68bf7-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="68bf7-115">本文中的範例可用於F#應用程式或F#腳本中。</span><span class="sxs-lookup"><span data-stu-id="68bf7-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="68bf7-116">若要建立F#腳本, 請在`.fsx` F#開發環境中建立`blobs.fsx`副檔名為的檔案, 例如。</span><span class="sxs-lookup"><span data-stu-id="68bf7-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="68bf7-117">接下來, 使用[Paket](https://fsprojects.github.io/Paket/)或`WindowsAzure.Storage` [NuGet](https://www.nuget.org/)之類的[套件管理員](package-management.md), 在您的`Microsoft.WindowsAzure.ConfigurationManager`腳本`Microsoft.WindowsAzure.Configuration.dll`中使用`WindowsAzure.Storage.dll` `#r`指示詞安裝和封裝和參考。</span><span class="sxs-lookup"><span data-stu-id="68bf7-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="68bf7-118">新增命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="68bf7-118">Add namespace declarations</span></span>

<span data-ttu-id="68bf7-119">將下列`open`語句新增至檔案頂端`blobs.fsx` :</span><span class="sxs-lookup"><span data-stu-id="68bf7-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="68bf7-120">取得您的連接字串</span><span class="sxs-lookup"><span data-stu-id="68bf7-120">Get your connection string</span></span>

<span data-ttu-id="68bf7-121">在本教學課程中, 您需要 Azure 儲存體連接字串。</span><span class="sxs-lookup"><span data-stu-id="68bf7-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="68bf7-122">如需連接字串的詳細資訊, 請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="68bf7-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="68bf7-123">在本教學課程中, 您會在腳本中輸入連接字串, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="68bf7-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="68bf7-124">不過, 這**不建議**用於實際的專案。</span><span class="sxs-lookup"><span data-stu-id="68bf7-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="68bf7-125">您的儲存體帳戶金鑰類似于儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="68bf7-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="68bf7-126">請務必小心保護您的儲存體帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="68bf7-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="68bf7-127">請避免將它散發給其他使用者、進行硬式編碼, 或將它儲存在其他人可以存取的純文字檔案中。</span><span class="sxs-lookup"><span data-stu-id="68bf7-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="68bf7-128">如果您認為金鑰可能遭到入侵, 您可以使用 Azure 入口網站重新產生金鑰。</span><span class="sxs-lookup"><span data-stu-id="68bf7-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="68bf7-129">對於實際的應用程式而言, 維護儲存體連接字串的最佳方式是在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="68bf7-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="68bf7-130">若要從設定檔提取連接字串, 您可以執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="68bf7-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="68bf7-131">使用 Azure Configuration Manager 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="68bf7-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="68bf7-132">您也可以使用 API (例如 .NET Framework 的`ConfigurationManager`類型)。</span><span class="sxs-lookup"><span data-stu-id="68bf7-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="68bf7-133">剖析連接字串</span><span class="sxs-lookup"><span data-stu-id="68bf7-133">Parse the connection string</span></span>

<span data-ttu-id="68bf7-134">若要剖析連接字串, 請使用:</span><span class="sxs-lookup"><span data-stu-id="68bf7-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="68bf7-135">這會傳回`CloudStorageAccount`。</span><span class="sxs-lookup"><span data-stu-id="68bf7-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="68bf7-136">建立一些本機虛擬資料</span><span class="sxs-lookup"><span data-stu-id="68bf7-136">Create some local dummy data</span></span>

<span data-ttu-id="68bf7-137">在開始之前, 請在腳本的目錄中建立一些虛擬的本機資料。</span><span class="sxs-lookup"><span data-stu-id="68bf7-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="68bf7-138">稍後您將上傳此資料。</span><span class="sxs-lookup"><span data-stu-id="68bf7-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="68bf7-139">建立 Blob 服務用戶端</span><span class="sxs-lookup"><span data-stu-id="68bf7-139">Create the Blob service client</span></span>

<span data-ttu-id="68bf7-140">`CloudBlobClient`型別可讓您抓取 blob 儲存體中儲存的容器和 blob。</span><span class="sxs-lookup"><span data-stu-id="68bf7-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="68bf7-141">以下是建立服務用戶端的其中一種方式:</span><span class="sxs-lookup"><span data-stu-id="68bf7-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="68bf7-142">現在您已準備好撰寫程式碼, 以讀取資料並將資料寫入至 Blob 儲存體。</span><span class="sxs-lookup"><span data-stu-id="68bf7-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="68bf7-143">建立容器</span><span class="sxs-lookup"><span data-stu-id="68bf7-143">Create a container</span></span>

<span data-ttu-id="68bf7-144">這個範例示範如何建立容器 (如果尚未存在):</span><span class="sxs-lookup"><span data-stu-id="68bf7-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="68bf7-145">根據預設, 新的容器是私用的, 這表示您必須指定儲存體存取金鑰, 才能從此容器下載 blob。</span><span class="sxs-lookup"><span data-stu-id="68bf7-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="68bf7-146">如果您想要讓所有人都能使用容器中的檔案, 您可以使用下列程式碼將容器設定為公用:</span><span class="sxs-lookup"><span data-stu-id="68bf7-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="68bf7-147">網際網路上的任何人都可以看到公用容器中的 blob, 但只有在您擁有適當的帳戶存取金鑰或共用存取簽章時, 才可以修改或刪除它們。</span><span class="sxs-lookup"><span data-stu-id="68bf7-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="68bf7-148">將 blob 上傳至容器</span><span class="sxs-lookup"><span data-stu-id="68bf7-148">Upload a blob into a container</span></span>

<span data-ttu-id="68bf7-149">Azure Blob 儲存體支援區塊 blob 和分頁 blob。</span><span class="sxs-lookup"><span data-stu-id="68bf7-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="68bf7-150">在大部分情況下, 建議使用區塊 blob 的類型。</span><span class="sxs-lookup"><span data-stu-id="68bf7-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="68bf7-151">若要將檔案上傳至區塊 blob, 請取得容器參考, 並使用它來取得區塊 blob 參考。</span><span class="sxs-lookup"><span data-stu-id="68bf7-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="68bf7-152">一旦擁有 blob 參考之後, 您就可以藉由呼叫`UploadFromFile`方法, 將任何資料流程上傳至其中。</span><span class="sxs-lookup"><span data-stu-id="68bf7-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="68bf7-153">如果 blob 先前不存在, 此作業會加以建立, 如果存在, 則會加以覆寫。</span><span class="sxs-lookup"><span data-stu-id="68bf7-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="68bf7-154">列出容器中的 blob</span><span class="sxs-lookup"><span data-stu-id="68bf7-154">List the blobs in a container</span></span>

<span data-ttu-id="68bf7-155">若要列出容器中的 blob, 請先取得容器參考。</span><span class="sxs-lookup"><span data-stu-id="68bf7-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="68bf7-156">然後, 您可以使用容器的`ListBlobs`方法來抓取 blob 和 (或) 其中的目錄。</span><span class="sxs-lookup"><span data-stu-id="68bf7-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="68bf7-157">若要`IListBlobItem`存取所傳回之的一組豐富屬性和方法, 您必須將它轉換`CloudBlockBlob`成、 `CloudPageBlob`或`CloudBlobDirectory`物件。</span><span class="sxs-lookup"><span data-stu-id="68bf7-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="68bf7-158">如果類型是未知的, 您可以使用類型檢查來決定要將它轉換成哪一個。</span><span class="sxs-lookup"><span data-stu-id="68bf7-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="68bf7-159">下列程式碼示範如何抓取和輸出`mydata`容器中每個專案的 URI:</span><span class="sxs-lookup"><span data-stu-id="68bf7-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="68bf7-160">您也可以在名稱中命名包含路徑資訊的 blob。</span><span class="sxs-lookup"><span data-stu-id="68bf7-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="68bf7-161">這會建立一個虛擬目錄結構, 您可以像使用傳統檔案系統一樣進行組織和進行管理。</span><span class="sxs-lookup"><span data-stu-id="68bf7-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="68bf7-162">請注意, 目錄結構僅限虛擬, Blob 儲存體中唯一可用的資源為容器和 blob。</span><span class="sxs-lookup"><span data-stu-id="68bf7-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="68bf7-163">不過, 儲存體用戶端程式庫提供`CloudBlobDirectory`一個物件來參照虛擬目錄, 並簡化以這種方式組織之 blob 的處理常式。</span><span class="sxs-lookup"><span data-stu-id="68bf7-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="68bf7-164">例如, 在名為`photos`的容器中, 請考慮下列一組區塊 blob:</span><span class="sxs-lookup"><span data-stu-id="68bf7-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="68bf7-165">*photo1.jpg*</span><span class="sxs-lookup"><span data-stu-id="68bf7-165">*photo1.jpg*</span></span>\
<span data-ttu-id="68bf7-166">*2015/架構/描述 .txt*</span><span class="sxs-lookup"><span data-stu-id="68bf7-166">*2015/architecture/description.txt*</span></span>\
<span data-ttu-id="68bf7-167">*2015/架構/photo3 .jpg*</span><span class="sxs-lookup"><span data-stu-id="68bf7-167">*2015/architecture/photo3.jpg*</span></span>\
<span data-ttu-id="68bf7-168">*2015/架構/photo4 .jpg*</span><span class="sxs-lookup"><span data-stu-id="68bf7-168">*2015/architecture/photo4.jpg*</span></span>\
<span data-ttu-id="68bf7-169">*2016/架構/photo5 .jpg*</span><span class="sxs-lookup"><span data-stu-id="68bf7-169">*2016/architecture/photo5.jpg*</span></span>\
<span data-ttu-id="68bf7-170">*2016/架構/photo6 .jpg*</span><span class="sxs-lookup"><span data-stu-id="68bf7-170">*2016/architecture/photo6.jpg*</span></span>\
<span data-ttu-id="68bf7-171">*2016/架構/描述 .txt*</span><span class="sxs-lookup"><span data-stu-id="68bf7-171">*2016/architecture/description.txt*</span></span>\
<span data-ttu-id="68bf7-172">*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="68bf7-172">*2016/photo7.jpg*</span></span>\

<span data-ttu-id="68bf7-173">當您在`ListBlobs`容器上呼叫 (如上述範例所示) 時, 會傳回階層式清單。</span><span class="sxs-lookup"><span data-stu-id="68bf7-173">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="68bf7-174">如果它同時`CloudBlobDirectory`包含和`CloudBlockBlob`物件, 分別代表容器中的目錄和 blob, 則產生的輸出看起來會像這樣:</span><span class="sxs-lookup"><span data-stu-id="68bf7-174">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="68bf7-175">(選擇性) 您可以將`UseFlatBlobListing` `ListBlobs`方法的參數設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="68bf7-175">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="68bf7-176">在此情況下, 容器中的每個 blob 都會以`CloudBlockBlob`物件的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="68bf7-176">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="68bf7-177">對的呼叫`ListBlobs`會傳回一般清單, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="68bf7-177">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="68bf7-178">而且, 視容器的目前內容而定, 結果如下所示:</span><span class="sxs-lookup"><span data-stu-id="68bf7-178">and, depending on the current contents of your container, the results look like this:</span></span>

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a><span data-ttu-id="68bf7-179">下載 blob</span><span class="sxs-lookup"><span data-stu-id="68bf7-179">Download blobs</span></span>

<span data-ttu-id="68bf7-180">若要下載 blob, 請先取出 blob 參考, 然後再`DownloadToStream`呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="68bf7-180">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="68bf7-181">下列範例會使用`DownloadToStream`方法, 將 blob 內容傳送給資料流程物件, 然後您可以將它保存到本機檔案。</span><span class="sxs-lookup"><span data-stu-id="68bf7-181">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="68bf7-182">您也可以使用`DownloadToStream`方法, 將 blob 的內容下載為文字字串。</span><span class="sxs-lookup"><span data-stu-id="68bf7-182">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="68bf7-183">刪除 blob</span><span class="sxs-lookup"><span data-stu-id="68bf7-183">Delete blobs</span></span>

<span data-ttu-id="68bf7-184">若要刪除 blob, 請先取得 blob 參考, 然後在其`Delete`上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="68bf7-184">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="68bf7-185">以非同步方式列出頁面中的 blob</span><span class="sxs-lookup"><span data-stu-id="68bf7-185">List blobs in pages asynchronously</span></span>

<span data-ttu-id="68bf7-186">如果您要列出大量的 blob, 或想要控制在一個列出作業中傳回的結果數目, 您可以在結果頁面中列出 blob。</span><span class="sxs-lookup"><span data-stu-id="68bf7-186">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="68bf7-187">這個範例示範如何以非同步方式傳回頁面中的結果, 以便在等候傳回大量結果時不會封鎖執行。</span><span class="sxs-lookup"><span data-stu-id="68bf7-187">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="68bf7-188">這個範例會顯示一般 blob 清單, 但您也可以藉由將`useFlatBlobListing` `ListBlobsSegmentedAsync`方法的參數設定為`false`, 來執行階層式清單。</span><span class="sxs-lookup"><span data-stu-id="68bf7-188">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="68bf7-189">此範例會使用`async`區塊來定義非同步方法。</span><span class="sxs-lookup"><span data-stu-id="68bf7-189">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="68bf7-190">``let!``關鍵字會暫停執行範例方法, 直到清單工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="68bf7-190">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="68bf7-191">我們現在可以使用這個非同步常式, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="68bf7-191">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="68bf7-192">首先上傳一些虛擬資料 (使用本教學課程稍早建立的本機檔案)。</span><span class="sxs-lookup"><span data-stu-id="68bf7-192">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="68bf7-193">現在, 請呼叫常式。</span><span class="sxs-lookup"><span data-stu-id="68bf7-193">Now, call the routine.</span></span> <span data-ttu-id="68bf7-194">您可以`Async.RunSynchronously`使用來強制執行非同步作業。</span><span class="sxs-lookup"><span data-stu-id="68bf7-194">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="68bf7-195">寫入附加 blob</span><span class="sxs-lookup"><span data-stu-id="68bf7-195">Writing to an append blob</span></span>

<span data-ttu-id="68bf7-196">附加 blob 已針對附加作業優化, 例如記錄。</span><span class="sxs-lookup"><span data-stu-id="68bf7-196">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="68bf7-197">如同區塊 blob, 附加 blob 是由區塊所組成, 但當您將新區塊新增至附加 blob 時, 一律會將它附加至 blob 的結尾。</span><span class="sxs-lookup"><span data-stu-id="68bf7-197">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="68bf7-198">您無法更新或刪除附加 blob 中的現有區塊。</span><span class="sxs-lookup"><span data-stu-id="68bf7-198">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="68bf7-199">附加 blob 的區塊識別碼不會公開, 因為它們是用於區塊 blob。</span><span class="sxs-lookup"><span data-stu-id="68bf7-199">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="68bf7-200">附加 blob 中的每個區塊可以是不同的大小, 最多 4 MB, 而附加 blob 最多可包含50000個區塊。</span><span class="sxs-lookup"><span data-stu-id="68bf7-200">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="68bf7-201">因此, 附加 blob 的大小上限會稍微超過 195 GB (4 MB X 50000 區塊)。</span><span class="sxs-lookup"><span data-stu-id="68bf7-201">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="68bf7-202">下列範例會建立新的附加 blob, 並在其中附加一些資料, 以模擬簡單的記錄作業。</span><span class="sxs-lookup"><span data-stu-id="68bf7-202">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="68bf7-203">如需這三種 blob 類型之間差異的詳細資訊, 請參閱[瞭解區塊 blob、分頁 blob 和附加 blob](https://msdn.microsoft.com/library/azure/ee691964.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="68bf7-203">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="68bf7-204">平行存取</span><span class="sxs-lookup"><span data-stu-id="68bf7-204">Concurrent access</span></span>

<span data-ttu-id="68bf7-205">若要支援從多個用戶端或多個進程實例平行存取 blob, 您可以使用**etag**或**租用**。</span><span class="sxs-lookup"><span data-stu-id="68bf7-205">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="68bf7-206">**Etag** -提供方法來偵測 blob 或容器已由另一個進程修改過</span><span class="sxs-lookup"><span data-stu-id="68bf7-206">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="68bf7-207">**租用**-提供一段時間取得對 blob 的獨佔、可續訂、寫入或刪除存取權的方法</span><span class="sxs-lookup"><span data-stu-id="68bf7-207">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="68bf7-208">如需詳細資訊, 請參閱[管理 Microsoft Azure 儲存體中的並行](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)存取。</span><span class="sxs-lookup"><span data-stu-id="68bf7-208">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="68bf7-209">命名容器</span><span class="sxs-lookup"><span data-stu-id="68bf7-209">Naming containers</span></span>

<span data-ttu-id="68bf7-210">Azure 儲存體中的每個 blob 都必須位於容器中。</span><span class="sxs-lookup"><span data-stu-id="68bf7-210">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="68bf7-211">容器會形成 blob 名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="68bf7-211">The container forms part of the blob name.</span></span> <span data-ttu-id="68bf7-212">例如, `mydata`是這些範例 blob uri 中容器的名稱:</span><span class="sxs-lookup"><span data-stu-id="68bf7-212">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

- https://storagesample.blob.core.windows.net/mydata/blob1.txt
- https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="68bf7-213">容器名稱必須是有效的 DNS 名稱, 符合下列命名規則:</span><span class="sxs-lookup"><span data-stu-id="68bf7-213">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="68bf7-214">容器名稱必須以字母或數位開頭, 且只能包含字母、數位和虛線 (-) 字元。</span><span class="sxs-lookup"><span data-stu-id="68bf7-214">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="68bf7-215">每個虛線 (-) 字元的前後都必須是字母或數位;容器名稱中不允許連續的連字號。</span><span class="sxs-lookup"><span data-stu-id="68bf7-215">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="68bf7-216">容器名稱中的所有字母都必須是小寫。</span><span class="sxs-lookup"><span data-stu-id="68bf7-216">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="68bf7-217">容器名稱的長度必須介於3到63個字元之間。</span><span class="sxs-lookup"><span data-stu-id="68bf7-217">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="68bf7-218">請注意, 容器的名稱必須一律為小寫。</span><span class="sxs-lookup"><span data-stu-id="68bf7-218">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="68bf7-219">如果您在容器名稱中包含大寫字母, 或違反容器命名規則, 您可能會收到400錯誤 (不正確的要求)。</span><span class="sxs-lookup"><span data-stu-id="68bf7-219">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="68bf7-220">管理 blob 的安全性</span><span class="sxs-lookup"><span data-stu-id="68bf7-220">Managing security for blobs</span></span>

<span data-ttu-id="68bf7-221">根據預設, Azure 儲存體會限制擁有帳戶存取金鑰的帳戶擁有者存取權, 以確保您的資料安全。</span><span class="sxs-lookup"><span data-stu-id="68bf7-221">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="68bf7-222">當您需要共用儲存體帳戶中的 blob 資料時, 請務必這麼做, 而不會危及帳戶存取金鑰的安全性。</span><span class="sxs-lookup"><span data-stu-id="68bf7-222">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="68bf7-223">此外, 您可以加密 blob 資料, 以確保它在網路上和 Azure 儲存體中都是安全的。</span><span class="sxs-lookup"><span data-stu-id="68bf7-223">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="68bf7-224">控制 blob 資料的存取</span><span class="sxs-lookup"><span data-stu-id="68bf7-224">Controlling access to blob data</span></span>

<span data-ttu-id="68bf7-225">根據預設, 儲存體帳戶中的 blob 資料只能供儲存體帳戶擁有者存取。</span><span class="sxs-lookup"><span data-stu-id="68bf7-225">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="68bf7-226">根據預設, 對 Blob 儲存體驗證要求時需要帳戶存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="68bf7-226">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="68bf7-227">不過, 您可能會想要將某些 blob 資料提供給其他使用者。</span><span class="sxs-lookup"><span data-stu-id="68bf7-227">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="68bf7-228">加密 blob 資料</span><span class="sxs-lookup"><span data-stu-id="68bf7-228">Encrypting blob data</span></span>

<span data-ttu-id="68bf7-229">Azure 儲存體支援在用戶端和伺服器上加密 blob 資料。</span><span class="sxs-lookup"><span data-stu-id="68bf7-229">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="68bf7-230">後續步驟</span><span class="sxs-lookup"><span data-stu-id="68bf7-230">Next steps</span></span>

<span data-ttu-id="68bf7-231">既然您已瞭解 Blob 儲存體的基本概念, 請參考下列連結以深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="68bf7-231">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="68bf7-232">工具</span><span class="sxs-lookup"><span data-stu-id="68bf7-232">Tools</span></span>

- <span data-ttu-id="68bf7-233">[F#AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span><span class="sxs-lookup"><span data-stu-id="68bf7-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span></span>\
<span data-ttu-id="68bf7-234">一F#種類型提供者, 可用來探索 Blob、資料表和佇列 Azure 儲存體資產, 並輕鬆地對其套用 CRUD 作業。</span><span class="sxs-lookup"><span data-stu-id="68bf7-234">An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="68bf7-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span><span class="sxs-lookup"><span data-stu-id="68bf7-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span></span>\
<span data-ttu-id="68bf7-236">使用F# Microsoft Azure 表格儲存體服務的 API</span><span class="sxs-lookup"><span data-stu-id="68bf7-236">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="68bf7-237">[Microsoft Azure 儲存體總管 (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span><span class="sxs-lookup"><span data-stu-id="68bf7-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span></span>\
<span data-ttu-id="68bf7-238">Microsoft 提供的免費獨立應用程式, 可讓您在 Windows、OS X 和 Linux 上以視覺化方式處理 Azure 儲存體資料。</span><span class="sxs-lookup"><span data-stu-id="68bf7-238">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="68bf7-239">Blob 儲存體參考</span><span class="sxs-lookup"><span data-stu-id="68bf7-239">Blob storage reference</span></span>

- [<span data-ttu-id="68bf7-240">適用于 .NET 的 Azure 儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="68bf7-240">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="68bf7-241">Azure 儲存體 Services REST API 參考</span><span class="sxs-lookup"><span data-stu-id="68bf7-241">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="68bf7-242">相關指南</span><span class="sxs-lookup"><span data-stu-id="68bf7-242">Related guides</span></span>

- [<span data-ttu-id="68bf7-243">使用 Azure Blob 儲存體的消費者入門C#</span><span class="sxs-lookup"><span data-stu-id="68bf7-243">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="68bf7-244">在 Windows 上使用 AzCopy 命令列公用程式傳輸資料</span><span class="sxs-lookup"><span data-stu-id="68bf7-244">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="68bf7-245">使用 Linux 上的 AzCopy 命令列公用程式傳輸資料</span><span class="sxs-lookup"><span data-stu-id="68bf7-245">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="68bf7-246">設定 Azure 儲存體連接字串</span><span class="sxs-lookup"><span data-stu-id="68bf7-246">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="68bf7-247">Azure 儲存體小組的 Blog</span><span class="sxs-lookup"><span data-stu-id="68bf7-247">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="68bf7-248">快速入門：使用 .NET 在物件儲存體中建立 blob</span><span class="sxs-lookup"><span data-stu-id="68bf7-248">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
