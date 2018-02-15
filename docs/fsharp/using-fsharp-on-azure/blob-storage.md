---
title: "開始使用 Azure Blob 儲存體使用 F #"
description: "搭配 Azure Blob 儲存體在雲端中儲存非結構化的資料。"
keywords: "visual f #、 f #，功能性程式設計，.NET 中，.NET Core，Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c5b74a4f-dcd1-4849-930c-904b6c8a04e1
ms.openlocfilehash: 9011bdceabd1b5e0541ecb94f3e812871688025b
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2018
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="46e16-104">開始使用 Azure Blob 儲存體使用 F #</span><span class="sxs-lookup"><span data-stu-id="46e16-104">Get started with Azure Blob storage using F#</span></span> #

<span data-ttu-id="46e16-105">Azure Blob 儲存體是可將非結構化的資料儲存在雲端作為物件/Blob 的服務。</span><span class="sxs-lookup"><span data-stu-id="46e16-105">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="46e16-106">Blob 儲存體可以儲存任何類型的文字或二進位資料，例如文件、媒體檔案或應用程式安裝程式。</span><span class="sxs-lookup"><span data-stu-id="46e16-106">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="46e16-107">Blob 儲存體也稱為物件儲存體。</span><span class="sxs-lookup"><span data-stu-id="46e16-107">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="46e16-108">這篇文章會示範如何使用 Blob 儲存體執行一般工作。</span><span class="sxs-lookup"><span data-stu-id="46e16-108">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="46e16-109">這些範例會使用 F # 使用適用於.NET 的 Azure 儲存體用戶端程式庫所撰寫的。</span><span class="sxs-lookup"><span data-stu-id="46e16-109">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="46e16-110">涵蓋的工作包括如何上傳、 列出、 下載及刪除 blob。</span><span class="sxs-lookup"><span data-stu-id="46e16-110">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="46e16-111">Blob 儲存體概念的概觀，請參閱[blob 儲存體的.NET 指南](/azure/storage/storage-dotnet-how-to-use-blobs)。</span><span class="sxs-lookup"><span data-stu-id="46e16-111">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="46e16-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="46e16-112">Prerequisites</span></span>

<span data-ttu-id="46e16-113">若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。</span><span class="sxs-lookup"><span data-stu-id="46e16-113">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="46e16-114">您也會需要此帳戶的儲存體存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="46e16-114">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="46e16-115">建立 F # 指令碼，並開始 F # Interactive</span><span class="sxs-lookup"><span data-stu-id="46e16-115">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="46e16-116">這篇文章中的範例可以用於 F # 應用程式或 F # 指令碼。</span><span class="sxs-lookup"><span data-stu-id="46e16-116">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="46e16-117">若要建立 F # 指令碼，建立檔案之`.fsx`擴充功能，例如`blobs.fsx`，F # 開發環境中。</span><span class="sxs-lookup"><span data-stu-id="46e16-117">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="46e16-118">接下來，使用[封裝管理員](package-management.md)例如[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`和`Microsoft.WindowsAzure.ConfigurationManager`封裝和參考`WindowsAzure.Storage.dll`和`Microsoft.WindowsAzure.Configuration.dll`在指令碼中使用`#r`指示詞。</span><span class="sxs-lookup"><span data-stu-id="46e16-118">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="46e16-119">加入命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="46e16-119">Add namespace declarations</span></span>

<span data-ttu-id="46e16-120">加入下列`open`上方的陳述式`blobs.fsx`檔案：</span><span class="sxs-lookup"><span data-stu-id="46e16-120">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="46e16-121">取得連接字串</span><span class="sxs-lookup"><span data-stu-id="46e16-121">Get your connection string</span></span>

<span data-ttu-id="46e16-122">您在本教學課程需要 Azure 儲存體連接字串。</span><span class="sxs-lookup"><span data-stu-id="46e16-122">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="46e16-123">如需連接字串的詳細資訊，請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="46e16-123">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="46e16-124">教學課程中，您可以輸入您的連接字串中指令碼中，像這樣：</span><span class="sxs-lookup"><span data-stu-id="46e16-124">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="46e16-125">不過，這是**不建議**用於真實的專案。</span><span class="sxs-lookup"><span data-stu-id="46e16-125">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="46e16-126">儲存體帳戶金鑰是類似於儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="46e16-126">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="46e16-127">一律為保護您的儲存體帳戶金鑰，請小心。</span><span class="sxs-lookup"><span data-stu-id="46e16-127">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="46e16-128">避免將其散發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。</span><span class="sxs-lookup"><span data-stu-id="46e16-128">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="46e16-129">您可以重新產生您使用 Azure 入口網站，如果您認為可能已受到危害的金鑰。</span><span class="sxs-lookup"><span data-stu-id="46e16-129">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="46e16-130">用於真實的應用程式，以維護您的儲存體連接字串的最佳方式是在組態檔中。</span><span class="sxs-lookup"><span data-stu-id="46e16-130">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="46e16-131">若要從組態檔擷取連接字串，您可以：</span><span class="sxs-lookup"><span data-stu-id="46e16-131">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="46e16-132">使用 Azure 組態管理員是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="46e16-132">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="46e16-133">您也可以使用例如.NET Framework API`ConfigurationManager`型別。</span><span class="sxs-lookup"><span data-stu-id="46e16-133">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="46e16-134">剖析連接字串</span><span class="sxs-lookup"><span data-stu-id="46e16-134">Parse the connection string</span></span>

<span data-ttu-id="46e16-135">若要剖析的連接字串，使用：</span><span class="sxs-lookup"><span data-stu-id="46e16-135">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="46e16-136">這會傳回`CloudStorageAccount`。</span><span class="sxs-lookup"><span data-stu-id="46e16-136">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="46e16-137">建立一些本機虛設資料</span><span class="sxs-lookup"><span data-stu-id="46e16-137">Create some local dummy data</span></span>

<span data-ttu-id="46e16-138">開始之前，建立一些虛擬的本機資料的指令碼目錄中。</span><span class="sxs-lookup"><span data-stu-id="46e16-138">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="46e16-139">稍後您上傳此資料。</span><span class="sxs-lookup"><span data-stu-id="46e16-139">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="46e16-140">建立 Blob 服務用戶端</span><span class="sxs-lookup"><span data-stu-id="46e16-140">Create the Blob service client</span></span>

<span data-ttu-id="46e16-141">`CloudBlobClient`類型可讓您擷取容器和 Blob 儲存體中的 blob。</span><span class="sxs-lookup"><span data-stu-id="46e16-141">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="46e16-142">以下是如何建立服務用戶端：</span><span class="sxs-lookup"><span data-stu-id="46e16-142">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="46e16-143">現在您已準備好開始撰寫程式碼中讀取的資料，並將資料寫入至 Blob 儲存體。</span><span class="sxs-lookup"><span data-stu-id="46e16-143">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="46e16-144">建立容器</span><span class="sxs-lookup"><span data-stu-id="46e16-144">Create a container</span></span>

<span data-ttu-id="46e16-145">這個範例示範如何建立容器，如果不存在：</span><span class="sxs-lookup"><span data-stu-id="46e16-145">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="46e16-146">根據預設，新的容器是私人的也就是說，您必須指定要從這個容器下載 blob 儲存體存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="46e16-146">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="46e16-147">如果您想要將容器內檔案提供給任何人，您可以設定容器必須是公用使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="46e16-147">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="46e16-148">在網際網路上的任何人都可以看到公用容器中的 blob，但您可以修改或刪除它們，只有當您擁有適當的帳戶存取金鑰或共用的存取簽章。</span><span class="sxs-lookup"><span data-stu-id="46e16-148">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="46e16-149">將 blob 上傳到容器</span><span class="sxs-lookup"><span data-stu-id="46e16-149">Upload a blob into a container</span></span>

<span data-ttu-id="46e16-150">Azure Blob 儲存體支援區塊 blob 和分頁 blob。</span><span class="sxs-lookup"><span data-stu-id="46e16-150">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="46e16-151">在大部分情況下，區塊 blob 是要使用的建議的類型。</span><span class="sxs-lookup"><span data-stu-id="46e16-151">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="46e16-152">若要上傳至區塊 blob 的檔案，取得為容器參考並使用它來取得區塊 blob 參考。</span><span class="sxs-lookup"><span data-stu-id="46e16-152">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="46e16-153">Blob 參考之後，您可以上傳資料的任何資料流，藉由呼叫`UploadFromFile`方法。</span><span class="sxs-lookup"><span data-stu-id="46e16-153">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="46e16-154">如果先前沒有存在，或覆寫它存在的話，這項作業會建立 blob。</span><span class="sxs-lookup"><span data-stu-id="46e16-154">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="46e16-155">列出容器中的 blob</span><span class="sxs-lookup"><span data-stu-id="46e16-155">List the blobs in a container</span></span>

<span data-ttu-id="46e16-156">若要列出容器中的 blob，先取得容器的參考。</span><span class="sxs-lookup"><span data-stu-id="46e16-156">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="46e16-157">然後，您可以使用容器的`ListBlobs`方法，以擷取 blob 及/或目錄內。</span><span class="sxs-lookup"><span data-stu-id="46e16-157">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="46e16-158">若要存取的屬性和方法傳回的一系列`IListBlobItem`，您必須將其轉換`CloudBlockBlob`， `CloudPageBlob`，或`CloudBlobDirectory`物件。</span><span class="sxs-lookup"><span data-stu-id="46e16-158">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="46e16-159">如果此類型為 unknown，您可以使用類型檢查來判斷哪些其轉型為。</span><span class="sxs-lookup"><span data-stu-id="46e16-159">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="46e16-160">下列程式碼示範如何擷取並輸出中的每個項目的 URI`mydata`容器：</span><span class="sxs-lookup"><span data-stu-id="46e16-160">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="46e16-161">您也可以在其名稱中的路徑資訊的 blob 名稱。</span><span class="sxs-lookup"><span data-stu-id="46e16-161">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="46e16-162">這會建立虛擬目錄結構，您可以組織及周遊如同傳統的檔案系統。</span><span class="sxs-lookup"><span data-stu-id="46e16-162">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="46e16-163">請注意，只是虛擬的目錄結構-Blob 儲存體中可用的唯一資源是容器和 blob。</span><span class="sxs-lookup"><span data-stu-id="46e16-163">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="46e16-164">不過，儲存體用戶端程式庫提供`CloudBlobDirectory`參照虛擬目錄，並簡化的 blob 會組織在這種方式，與處理序的物件。</span><span class="sxs-lookup"><span data-stu-id="46e16-164">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="46e16-165">例如，請考慮下列一名為的容器中的區塊 blob `photos`:</span><span class="sxs-lookup"><span data-stu-id="46e16-165">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="46e16-166">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="46e16-166">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="46e16-167">當您呼叫`ListBlobs`在容器使用時 （如同上述範例中），會傳回階層式清單。</span><span class="sxs-lookup"><span data-stu-id="46e16-167">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="46e16-168">如果它同時包含`CloudBlobDirectory`和`CloudBlockBlob`物件，代表目錄和 blob 容器中的，則產生的輸出看起來類似這樣：</span><span class="sxs-lookup"><span data-stu-id="46e16-168">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="46e16-169">您可以選擇性地設定`UseFlatBlobListing`參數`ListBlobs`方法`true`。</span><span class="sxs-lookup"><span data-stu-id="46e16-169">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="46e16-170">在此情況下，會以傳回容器中的每個 blob`CloudBlockBlob`物件。</span><span class="sxs-lookup"><span data-stu-id="46e16-170">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="46e16-171">若要呼叫`ListBlobs`返回一般清單看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="46e16-171">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="46e16-172">此外，根據您的容器目前的內容，而結果看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="46e16-172">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="46e16-173">下載 blob</span><span class="sxs-lookup"><span data-stu-id="46e16-173">Download blobs</span></span>

<span data-ttu-id="46e16-174">若要下載 blob，先擷取 blob 的參考，然後呼叫`DownloadToStream`方法。</span><span class="sxs-lookup"><span data-stu-id="46e16-174">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="46e16-175">下列範例會使用`DownloadToStream`方法來傳輸資料流物件，您可以再保存到本機檔案的 blob 內容。</span><span class="sxs-lookup"><span data-stu-id="46e16-175">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="46e16-176">您也可以使用`DownloadToStream`方法來下載為文字字串將 blob 的內容。</span><span class="sxs-lookup"><span data-stu-id="46e16-176">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="46e16-177">刪除 blob</span><span class="sxs-lookup"><span data-stu-id="46e16-177">Delete blobs</span></span>

<span data-ttu-id="46e16-178">若要刪除 blob，請先取得 blob 的參考，然後呼叫`Delete`方法。</span><span class="sxs-lookup"><span data-stu-id="46e16-178">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="46e16-179">以非同步方式列出網頁中的 blob</span><span class="sxs-lookup"><span data-stu-id="46e16-179">List blobs in pages asynchronously</span></span>

<span data-ttu-id="46e16-180">如果在列示大量的 blob，或您想要控制您在一個清單作業中傳回的結果數目，您可以列出結果的頁面中的 blob。</span><span class="sxs-lookup"><span data-stu-id="46e16-180">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="46e16-181">此範例顯示如何以非同步方式傳回的結果頁面中，以便等候傳回大量結果時不會封鎖執行。</span><span class="sxs-lookup"><span data-stu-id="46e16-181">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="46e16-182">此範例顯示一般 blob 清單，但您也可以藉由設定執行階層式清單，`useFlatBlobListing`參數`ListBlobsSegmentedAsync`方法`false`。</span><span class="sxs-lookup"><span data-stu-id="46e16-182">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="46e16-183">這個範例會定義非同步方法，使用`async`區塊。</span><span class="sxs-lookup"><span data-stu-id="46e16-183">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="46e16-184">``let!``關鍵字會暫停執行範例的方法，直到清單的工作完成。</span><span class="sxs-lookup"><span data-stu-id="46e16-184">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="46e16-185">我們現在可以使用這個非同步常式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="46e16-185">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="46e16-186">第一次您上傳某些虛擬資料 （使用稍早在本教學課程中建立的本機檔案）。</span><span class="sxs-lookup"><span data-stu-id="46e16-186">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="46e16-187">現在，呼叫常式。</span><span class="sxs-lookup"><span data-stu-id="46e16-187">Now, call the routine.</span></span> <span data-ttu-id="46e16-188">您使用``Async.RunSynchronously``來強制執行非同步作業。</span><span class="sxs-lookup"><span data-stu-id="46e16-188">You use ``Async.RunSynchronously`` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="46e16-189">要寫入附加 blob</span><span class="sxs-lookup"><span data-stu-id="46e16-189">Writing to an append blob</span></span>

<span data-ttu-id="46e16-190">附加 blob 最適合用於附加作業，例如記錄。</span><span class="sxs-lookup"><span data-stu-id="46e16-190">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="46e16-191">如區塊 blob、 附加 blob 區塊組成，但當您新增新的區塊附加 blob 時，它一定會附加到 blob 結尾。</span><span class="sxs-lookup"><span data-stu-id="46e16-191">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="46e16-192">您無法更新或刪除現有區塊附加 blob 中。</span><span class="sxs-lookup"><span data-stu-id="46e16-192">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="46e16-193">因為它們是區塊 blob，不會公開附加 blob 的區塊識別碼。</span><span class="sxs-lookup"><span data-stu-id="46e16-193">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="46e16-194">每個區塊中附加 blob 可以是不同的大小，最大值為 4 MB，而且附加 blob 不可包括最多 50,000 個區塊。</span><span class="sxs-lookup"><span data-stu-id="46e16-194">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="46e16-195">附加 blob 的大小上限，因此是稍微大於 195 GB （4 MB X 50000 區塊）。</span><span class="sxs-lookup"><span data-stu-id="46e16-195">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="46e16-196">下列範例會建立新的附加 blob，並將一些資料附加至它，模擬簡單的記錄作業。</span><span class="sxs-lookup"><span data-stu-id="46e16-196">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="46e16-197">請參閱[了解區塊 Blob、 分頁 Blob，並附加 Blob](https://msdn.microsoft.com/library/azure/ee691964.aspx)如需有關 blob 的三種類型之間的差異。</span><span class="sxs-lookup"><span data-stu-id="46e16-197">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="46e16-198">並行存取</span><span class="sxs-lookup"><span data-stu-id="46e16-198">Concurrent access</span></span>

<span data-ttu-id="46e16-199">若要支援的 blob 的並行存取，從多個用戶端或多個處理序執行個體，您可以使用**Etag**或**租用**。</span><span class="sxs-lookup"><span data-stu-id="46e16-199">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="46e16-200">**Etag** -提供方法來偵測 blob 或容器已修改的另一個處理序</span><span class="sxs-lookup"><span data-stu-id="46e16-200">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="46e16-201">**租用**-可用來取得獨佔、 更新、 寫入或刪除的一段時間的存取權的 blob</span><span class="sxs-lookup"><span data-stu-id="46e16-201">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="46e16-202">如需詳細資訊，請參閱[管理 Microsoft Azure 儲存體中的並行存取](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)。</span><span class="sxs-lookup"><span data-stu-id="46e16-202">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="46e16-203">命名的容器</span><span class="sxs-lookup"><span data-stu-id="46e16-203">Naming containers</span></span>

<span data-ttu-id="46e16-204">Azure 儲存體中的每個 blob 必須位於容器中。</span><span class="sxs-lookup"><span data-stu-id="46e16-204">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="46e16-205">容器的 blob 名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="46e16-205">The container forms part of the blob name.</span></span> <span data-ttu-id="46e16-206">例如，`mydata`的這些範例 blob Uri 中的容器名稱：</span><span class="sxs-lookup"><span data-stu-id="46e16-206">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="46e16-207">容器名稱必須是有效的 DNS 名稱，並且符合下列命名規則：</span><span class="sxs-lookup"><span data-stu-id="46e16-207">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="46e16-208">容器名稱必須以字母或數字開頭，而且只能包含字母、 數字和虛線 （-） 字元。</span><span class="sxs-lookup"><span data-stu-id="46e16-208">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="46e16-209">每個虛線 （-） 字元必須是立即之前和之後都是字母或數字。容器名稱中不允許連續虛線。</span><span class="sxs-lookup"><span data-stu-id="46e16-209">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="46e16-210">容器名稱中的所有字母都必須都是小寫。</span><span class="sxs-lookup"><span data-stu-id="46e16-210">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="46e16-211">容器名稱必須介於 3 到 63 個字元。</span><span class="sxs-lookup"><span data-stu-id="46e16-211">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="46e16-212">請注意，容器的名稱一律必須是小寫。</span><span class="sxs-lookup"><span data-stu-id="46e16-212">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="46e16-213">如果您在輸入容器名稱中包含一個大寫字母或違反命名規則的容器，您可能會收到 400 的錯誤 （不正確的要求）。</span><span class="sxs-lookup"><span data-stu-id="46e16-213">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="46e16-214">管理安全性的 blob</span><span class="sxs-lookup"><span data-stu-id="46e16-214">Managing security for blobs</span></span>

<span data-ttu-id="46e16-215">根據預設，Azure 儲存體會保留您的資料安全，方法是限制的存取權的帳戶擁有者，並且擁有帳戶存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="46e16-215">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="46e16-216">當您要共用儲存體帳戶中的 blob 資料時，請務必這樣做不會危及您的帳戶存取金鑰的安全性。</span><span class="sxs-lookup"><span data-stu-id="46e16-216">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="46e16-217">此外，您可以加密以確保它的安全性會透過網路與 Azure 儲存體中的 blob 資料。</span><span class="sxs-lookup"><span data-stu-id="46e16-217">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="46e16-218">控制對 blob 資料的存取</span><span class="sxs-lookup"><span data-stu-id="46e16-218">Controlling access to blob data</span></span>

<span data-ttu-id="46e16-219">根據預設，在儲存體帳戶的 blob 資料是只有儲存體帳戶擁有者可以存取。</span><span class="sxs-lookup"><span data-stu-id="46e16-219">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="46e16-220">根據預設，驗證要求，針對 Blob 儲存體需要帳戶存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="46e16-220">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="46e16-221">不過，您可能想要讓其他使用者使用特定的 blob 資料。</span><span class="sxs-lookup"><span data-stu-id="46e16-221">However, you might want to make certain blob data available to other users.</span></span>

<span data-ttu-id="46e16-222">如需如何控制存取 blob 儲存體的詳細資訊，請參閱[blob 儲存體 區段上存取控制.NET 手冊](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data)。</span><span class="sxs-lookup"><span data-stu-id="46e16-222">For details on how to control access to blob storage, see [the .NET guide for blob storage section on access control](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span></span>


### <a name="encrypting-blob-data"></a><span data-ttu-id="46e16-223">加密的 blob 資料</span><span class="sxs-lookup"><span data-stu-id="46e16-223">Encrypting blob data</span></span>

<span data-ttu-id="46e16-224">Azure 儲存體支援加密的用戶端和伺服器上的 blob 資料。</span><span class="sxs-lookup"><span data-stu-id="46e16-224">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

<span data-ttu-id="46e16-225">如需加密 blob 資料的詳細資訊，請參閱[blob 儲存體加密 區段的.NET 指南](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data)。</span><span class="sxs-lookup"><span data-stu-id="46e16-225">For details on encrypting blob data, see [the .NET guide for blob storage section on encryption](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span></span>

## <a name="next-steps"></a><span data-ttu-id="46e16-226">後續步驟</span><span class="sxs-lookup"><span data-stu-id="46e16-226">Next steps</span></span>

<span data-ttu-id="46e16-227">現在，您學到 Blob 儲存體的基本概念，請遵循下列連結，以進一步了解。</span><span class="sxs-lookup"><span data-stu-id="46e16-227">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="46e16-228">工具</span><span class="sxs-lookup"><span data-stu-id="46e16-228">Tools</span></span>
- <span data-ttu-id="46e16-229">[F # AzureStorageTypeProvider](http://fsprojects.github.io/AzureStorageTypeProvider/) F # 類型提供者可以用來瀏覽 Blob、 資料表和佇列的 Azure 儲存體資產，並輕鬆地套用在其上的 CRUD 作業。</span><span class="sxs-lookup"><span data-stu-id="46e16-229">[F# AzureStorageTypeProvider](http://fsprojects.github.io/AzureStorageTypeProvider/) An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>
- <span data-ttu-id="46e16-230">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) F # 應用程式開發介面使用 Microsoft Azure 資料表儲存體服務</span><span class="sxs-lookup"><span data-stu-id="46e16-230">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) An F# API for using Microsoft Azure Table Storage service</span></span>
- <span data-ttu-id="46e16-231">[Microsoft Azure 儲存體總管 (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)是免費的可讓您能夠以視覺化方式使用 Azure 儲存體資料在 Windows、 OS X 和 Linux 上的 microsoft 獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="46e16-231">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="46e16-232">Blob 儲存體參考</span><span class="sxs-lookup"><span data-stu-id="46e16-232">Blob storage reference</span></span>

- [<span data-ttu-id="46e16-233">適用於.NET 的 azure 儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="46e16-233">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="46e16-234">Azure 儲存體服務 REST API 參考</span><span class="sxs-lookup"><span data-stu-id="46e16-234">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="46e16-235">相關的輔助線</span><span class="sxs-lookup"><span data-stu-id="46e16-235">Related guides</span></span>

- [<span data-ttu-id="46e16-236">在 C# 中的 Azure Blob 儲存體使用者入門</span><span class="sxs-lookup"><span data-stu-id="46e16-236">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/documentation/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="46e16-237">使用 Windows 上的 AzCopy 命令列公用程式傳送資料</span><span class="sxs-lookup"><span data-stu-id="46e16-237">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="46e16-238">傳輸資料與 Linux 上的 AzCopy 命令列公用程式</span><span class="sxs-lookup"><span data-stu-id="46e16-238">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="46e16-239">設定 Azure 儲存體連接字串</span><span class="sxs-lookup"><span data-stu-id="46e16-239">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="46e16-240">Azure 儲存體團隊部落格</span><span class="sxs-lookup"><span data-stu-id="46e16-240">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
