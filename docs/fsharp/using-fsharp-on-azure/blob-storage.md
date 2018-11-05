---
title: 開始使用 F# 的 Azure Blob 儲存體
description: 使用 Azure Blob 儲存體在雲端中儲存非結構化的資料。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: ea9dc334ec9c2bcd4a80cc501d4b6634da5f64e4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "44037278"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="0b0cb-103">開始使用 F# 的 Azure Blob 儲存體</span><span class="sxs-lookup"><span data-stu-id="0b0cb-103">Get started with Azure Blob storage using F#</span></span> #

<span data-ttu-id="0b0cb-104">Azure Blob 儲存體是可將非結構化的資料儲存在雲端作為物件/Blob 的服務。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="0b0cb-105">Blob 儲存體可以儲存任何類型的文字或二進位資料，例如文件、媒體檔案或應用程式安裝程式。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="0b0cb-106">Blob 儲存體也稱為物件儲存體。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="0b0cb-107">這篇文章會示範如何使用 Blob 儲存體執行一般工作。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="0b0cb-108">範例會使用 F# 使用 Azure Storage Client Library for.NET 所撰寫的。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="0b0cb-109">涵蓋的工作包括如何上傳、 列出、 下載及刪除 blob。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="0b0cb-110">Blob 儲存體概念的概觀，請參閱 < [blob 儲存體的.NET 指南](/azure/storage/storage-dotnet-how-to-use-blobs)。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0b0cb-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="0b0cb-111">Prerequisites</span></span>

<span data-ttu-id="0b0cb-112">若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="0b0cb-113">您也會需要此帳戶的儲存體存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="0b0cb-114">建立 F# 指令碼，並開始 F# Interactive</span><span class="sxs-lookup"><span data-stu-id="0b0cb-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="0b0cb-115">這篇文章中的範例可以用於 F# 應用程式或 F# 指令碼。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="0b0cb-116">若要建立 F# 指令碼，建立的檔案`.fsx`擴充功能，例如`blobs.fsx`，F# 開發環境中。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="0b0cb-117">接下來，使用[套件管理員](package-management.md)這類[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`並`Microsoft.WindowsAzure.ConfigurationManager`套件和參考`WindowsAzure.Storage.dll`和`Microsoft.WindowsAzure.Configuration.dll`在指令碼中使用`#r`指示詞。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="0b0cb-118">加入命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="0b0cb-118">Add namespace declarations</span></span>

<span data-ttu-id="0b0cb-119">新增下列`open`陳述式的`blobs.fsx`檔案：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="0b0cb-120">取得連接字串</span><span class="sxs-lookup"><span data-stu-id="0b0cb-120">Get your connection string</span></span>

<span data-ttu-id="0b0cb-121">您在本教學課程需要 Azure 儲存體連接字串。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="0b0cb-122">如需有關連接字串的詳細資訊，請參閱 <<c0> [ 設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="0b0cb-123">教學課程中，您可以輸入您的連接字串中您的指令碼，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="0b0cb-124">不過，這是**不建議使用**實際的專案。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="0b0cb-125">儲存體帳戶金鑰很類似儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="0b0cb-126">請務必小心保護您的儲存體帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="0b0cb-127">請避免轉發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="0b0cb-128">您可以重新產生您使用 Azure 入口網站，如果您認為可能已遭盜用的金鑰。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="0b0cb-129">實際的應用程式，來維護您的儲存體連接字串的最佳方式是在組態檔中。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="0b0cb-130">若要從組態檔擷取連接字串，您可以這樣做：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="0b0cb-131">使用 Azure Configuration Manager 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="0b0cb-132">您也可以使用 API，例如.NET Framework 的`ConfigurationManager`型別。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="0b0cb-133">剖析連接字串</span><span class="sxs-lookup"><span data-stu-id="0b0cb-133">Parse the connection string</span></span>

<span data-ttu-id="0b0cb-134">若要剖析的連接字串，請使用：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="0b0cb-135">這會傳回`CloudStorageAccount`。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="0b0cb-136">建立一些本機的 dummy 資料</span><span class="sxs-lookup"><span data-stu-id="0b0cb-136">Create some local dummy data</span></span>

<span data-ttu-id="0b0cb-137">開始之前，請在我們的指令碼的目錄中建立一些假的本機資料。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="0b0cb-138">稍後您上傳此資料。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="0b0cb-139">建立 Blob 服務用戶端</span><span class="sxs-lookup"><span data-stu-id="0b0cb-139">Create the Blob service client</span></span>

<span data-ttu-id="0b0cb-140">`CloudBlobClient`類型可讓您擷取容器和 Blob 儲存體中的 blob。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="0b0cb-141">若要建立服務用戶端的其中一個方法如下：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="0b0cb-142">現在您已準備好撰寫程式碼來讀取資料，並將資料寫入至 Blob 儲存體。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="0b0cb-143">建立容器</span><span class="sxs-lookup"><span data-stu-id="0b0cb-143">Create a container</span></span>

<span data-ttu-id="0b0cb-144">此範例示範如何建立容器，如果不存在：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="0b0cb-145">根據預設，新容器屬私人的這表示您必須指定您的儲存體存取金鑰才能從此容器下載 blob。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="0b0cb-146">如果您想要在容器內的檔案提供給所有人，您可以將容器設定公開使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="0b0cb-147">在網際網路上的任何人都可以看到公用容器中的 blob，但您可以修改或刪除它們，只有當您擁有適當的帳戶存取金鑰或共用的存取簽章。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="0b0cb-148">將 blob 上傳至容器</span><span class="sxs-lookup"><span data-stu-id="0b0cb-148">Upload a blob into a container</span></span>

<span data-ttu-id="0b0cb-149">Azure Blob 儲存體支援區塊 blob 和分頁 blob。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="0b0cb-150">在大部分情況下，區塊 blob 是要使用的建議的類型。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="0b0cb-151">將檔案上傳至區塊 blob，取得容器參考，並使用它來取得區塊 blob 參考。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="0b0cb-152">Blob 參考之後，您可以上傳任何資料流，藉由呼叫`UploadFromFile`方法。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="0b0cb-153">如果先前未存在，或覆寫它，如果檔案存在，此作業就會建立 blob。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="0b0cb-154">列出容器中的 blob</span><span class="sxs-lookup"><span data-stu-id="0b0cb-154">List the blobs in a container</span></span>

<span data-ttu-id="0b0cb-155">若要列出容器中的 blob，請先取得容器參考。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="0b0cb-156">然後，您可以使用容器的`ListBlobs`方法來擷取 blob 和/或目錄。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="0b0cb-157">若要存取的屬性和方法傳回一組豐富`IListBlobItem`，您必須將它轉換成`CloudBlockBlob`， `CloudPageBlob`，或`CloudBlobDirectory`物件。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="0b0cb-158">如果類型是未知，您可以使用類型檢查來決定要將它轉換成。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="0b0cb-159">下列程式碼示範如何擷取和輸出中的每個項目的 URI`mydata`容器：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="0b0cb-160">您也可以在其名稱中的路徑資訊的 blob 名稱。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="0b0cb-161">這會建立虛擬目錄結構，您能夠組織及周遊，就像使用傳統檔案系統。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="0b0cb-162">請注意，只是虛擬目錄結構-唯一的 Blob 儲存體中的可用資源為容器和 blob。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="0b0cb-163">不過，儲存體用戶端程式庫提供`CloudBlobDirectory`物件來參照虛擬目錄，以及簡化這種方式組織 blob 所使用的程序。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="0b0cb-164">例如，請考慮下列一組區塊 blob 容器內`photos`:</span><span class="sxs-lookup"><span data-stu-id="0b0cb-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="0b0cb-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="0b0cb-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="0b0cb-166">當您呼叫`ListBlobs`（如同上述範例中） 的容器，會傳回階層式清單。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-166">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="0b0cb-167">如果它同時包含`CloudBlobDirectory`和`CloudBlockBlob`物件，代表目錄和 blob 容器中，分別則產生的輸出看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-167">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="0b0cb-168">您可以選擇性地設定`UseFlatBlobListing`的參數`ListBlobs`方法，以`true`。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-168">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="0b0cb-169">在此情況下，每個 blob 容器中的會傳回為`CloudBlockBlob`物件。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-169">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="0b0cb-170">若要呼叫`ListBlobs`傳回簡單列表看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-170">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="0b0cb-171">而且，根據您的容器目前的內容，結果看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-171">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="0b0cb-172">下載 blob</span><span class="sxs-lookup"><span data-stu-id="0b0cb-172">Download blobs</span></span>

<span data-ttu-id="0b0cb-173">若要下載 blob，請先擷取 blob 參考，然後呼叫`DownloadToStream`方法。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-173">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="0b0cb-174">下列範例會使用`DownloadToStream`方法，以將 blob 內容傳送到您可接著保留本機檔案的串流物件。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-174">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="0b0cb-175">您也可以使用`DownloadToStream`方法來下載 blob 的內容當成文字字串。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-175">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="0b0cb-176">刪除 blob</span><span class="sxs-lookup"><span data-stu-id="0b0cb-176">Delete blobs</span></span>

<span data-ttu-id="0b0cb-177">若要刪除 blob，請先取得 blob 參考，然後呼叫`Delete`在其上的方法。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-177">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="0b0cb-178">以非同步方式列出在頁面中的 blob</span><span class="sxs-lookup"><span data-stu-id="0b0cb-178">List blobs in pages asynchronously</span></span>

<span data-ttu-id="0b0cb-179">如果您要列出大量 blob，或您想要控制您在單一列出作業所傳回的結果數目，您可以列出結果頁面中的 blob。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-179">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="0b0cb-180">此範例會示範如何以非同步方式分頁傳回結果，以便等待傳回大型結果集而不會封鎖執行。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-180">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="0b0cb-181">此範例示範一般 blob 列出方式，但您也可以藉由設定執行階層式清單中，`useFlatBlobListing`的參數`ListBlobsSegmentedAsync`方法，以`false`。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-181">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="0b0cb-182">此範例會定義非同步方法，使用`async`區塊。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-182">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="0b0cb-183">``let!``關鍵字會暫停執行範例的方法，直到列出工作完成。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-183">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="0b0cb-184">我們現在可以使用這個非同步常式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-184">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="0b0cb-185">第一次您上傳一些假的資料 （使用稍早在本教學課程中建立的本機檔案）。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-185">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="0b0cb-186">現在，呼叫的常式。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-186">Now, call the routine.</span></span> <span data-ttu-id="0b0cb-187">您使用`Async.RunSynchronously`來強制執行非同步作業。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-187">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="0b0cb-188">寫入至附加 blob</span><span class="sxs-lookup"><span data-stu-id="0b0cb-188">Writing to an append blob</span></span>

<span data-ttu-id="0b0cb-189">附加 blob 已針對附加作業，例如記錄最佳化。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-189">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="0b0cb-190">如同區塊 blob、 附加 blob 由區塊組成，但當您將新區塊加入附加 blob 時，它一律會附加到 blob 結尾。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-190">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="0b0cb-191">您無法更新或刪除附加 blob 中的現有區塊。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-191">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="0b0cb-192">附加 blob 的區塊識別碼不會公開的區塊 blob。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-192">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="0b0cb-193">附加 blob 中的每個區塊可以是不同的大小，最多為 4 MB，並附加 blob 可包含最多 50,000 個區塊。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-193">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="0b0cb-194">附加 blob 的大小上限，因此是稍高於 195 GB （4 MB 個區塊）。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-194">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="0b0cb-195">下列範例會建立新的附加 blob，並附加一些資料，來模擬簡單的記錄作業。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-195">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="0b0cb-196">請參閱[了解區塊 Blob、 分頁 Blob 和附加 Blob](https://msdn.microsoft.com/library/azure/ee691964.aspx)如需有關 blob 的三種類型之間的差異。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-196">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="0b0cb-197">並行存取</span><span class="sxs-lookup"><span data-stu-id="0b0cb-197">Concurrent access</span></span>

<span data-ttu-id="0b0cb-198">若要支援並行存取的 blob，從多個用戶端或多個處理序執行個體，您可以使用**Etag**或是**租用**。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-198">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="0b0cb-199">**Etag** -提供一個方式來偵測 blob 或容器，已修改另一個處理序</span><span class="sxs-lookup"><span data-stu-id="0b0cb-199">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="0b0cb-200">**租用**-可用來取得獨佔、 可更新、 寫入或刪除 blob 的存取權的一段時間</span><span class="sxs-lookup"><span data-stu-id="0b0cb-200">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="0b0cb-201">如需詳細資訊，請參閱 <<c0> [ 管理 Microsoft Azure 儲存體中的並行存取](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-201">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="0b0cb-202">命名的容器</span><span class="sxs-lookup"><span data-stu-id="0b0cb-202">Naming containers</span></span>

<span data-ttu-id="0b0cb-203">Azure 儲存體中的每個 blob 必須位於一個容器。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-203">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="0b0cb-204">此容器會組成 blob 名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-204">The container forms part of the blob name.</span></span> <span data-ttu-id="0b0cb-205">比方說，`mydata`的這些範例 blob Uri 中的容器名稱：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-205">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="0b0cb-206">容器名稱必須是有效的 DNS 名稱，且符合下列命名規則：</span><span class="sxs-lookup"><span data-stu-id="0b0cb-206">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="0b0cb-207">容器名稱必須以字母或數字開頭，並且可包含字母、 數字和虛線 （-） 字元。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-207">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="0b0cb-208">每個虛線 （-） 字元必須是立即前面和後面接著字母或數字，容器名稱中不允許連續虛線。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-208">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="0b0cb-209">容器名稱中的所有字母必須都是小寫。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-209">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="0b0cb-210">容器名稱必須介於 3 至 63 個字元。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-210">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="0b0cb-211">請注意，容器的名稱一律必須小寫。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-211">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="0b0cb-212">如果您輸入容器名稱中包含大寫字母或其他違反容器命名規則，您可能會收到 400 錯誤 （不正確的要求）。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-212">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="0b0cb-213">管理 blob 安全性</span><span class="sxs-lookup"><span data-stu-id="0b0cb-213">Managing security for blobs</span></span>

<span data-ttu-id="0b0cb-214">根據預設，Azure 儲存體會保持資料安全限制的存取帳戶擁有者的帳戶存取金鑰的擁有權。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-214">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="0b0cb-215">當您需要共用儲存體帳戶中的 blob 資料時，很重要，若要這樣做不會危及您帳戶存取金鑰的安全性。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-215">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="0b0cb-216">此外，您可以加密 blob 資料，以確保它是安全會透過網路與 Azure 儲存體中。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-216">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="0b0cb-217">控制對 blob 資料的存取</span><span class="sxs-lookup"><span data-stu-id="0b0cb-217">Controlling access to blob data</span></span>

<span data-ttu-id="0b0cb-218">根據預設，在儲存體帳戶的 blob 資料是只有儲存體帳戶擁有者可以存取。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-218">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="0b0cb-219">根據預設，驗證對 Blob 儲存體的要求需要帳戶存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-219">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="0b0cb-220">不過，您可能會想讓其他使用者使用特定的 blob 資料。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-220">However, you might want to make certain blob data available to other users.</span></span>

<span data-ttu-id="0b0cb-221">如需如何控制對 blob 儲存體的詳細資訊，請參閱 <<c0> [ 存取控制的 blob 儲存體 區段的.NET 指南](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data)。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-221">For details on how to control access to blob storage, see [the .NET guide for blob storage section on access control](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span></span>


### <a name="encrypting-blob-data"></a><span data-ttu-id="0b0cb-222">加密 blob 資料</span><span class="sxs-lookup"><span data-stu-id="0b0cb-222">Encrypting blob data</span></span>

<span data-ttu-id="0b0cb-223">Azure 儲存體支援加密在用戶端和伺服器上的 blob 資料。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-223">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

<span data-ttu-id="0b0cb-224">如需加密 blob 資料的詳細資訊，請參閱[加密的 blob 儲存體區段的.NET 指南](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data)。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-224">For details on encrypting blob data, see [the .NET guide for blob storage section on encryption](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0b0cb-225">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0b0cb-225">Next steps</span></span>

<span data-ttu-id="0b0cb-226">既然您已了解 Blob 儲存體的基本概念，請遵循下列連結以了解更多。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-226">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="0b0cb-227">工具</span><span class="sxs-lookup"><span data-stu-id="0b0cb-227">Tools</span></span>
- <span data-ttu-id="0b0cb-228">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) F# 型別提供者可用來瀏覽 Blob、 資料表和佇列的 Azure 儲存體資產，並輕鬆地套用在其上的 CRUD 作業。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-228">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>
- <span data-ttu-id="0b0cb-229">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) F# API 使用 Microsoft Azure 資料表儲存體服務</span><span class="sxs-lookup"><span data-stu-id="0b0cb-229">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) An F# API for using Microsoft Azure Table Storage service</span></span>
- <span data-ttu-id="0b0cb-230">[Microsoft Azure 儲存體總管 (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)是免費的獨立應用程式，可讓您在 Windows、 OSX 和 Linux 上以視覺化方式處理 Azure 儲存體資料。</span><span class="sxs-lookup"><span data-stu-id="0b0cb-230">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="0b0cb-231">Blob 儲存體參考</span><span class="sxs-lookup"><span data-stu-id="0b0cb-231">Blob storage reference</span></span>

- [<span data-ttu-id="0b0cb-232">適用於.NET 的 azure 儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="0b0cb-232">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="0b0cb-233">Azure 儲存體服務 REST API 參考</span><span class="sxs-lookup"><span data-stu-id="0b0cb-233">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="0b0cb-234">相關的輔助線</span><span class="sxs-lookup"><span data-stu-id="0b0cb-234">Related guides</span></span>

- [<span data-ttu-id="0b0cb-235">開始使用 C# 中的 Azure Blob 儲存體</span><span class="sxs-lookup"><span data-stu-id="0b0cb-235">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="0b0cb-236">Windows 上的 AzCopy 命令列公用程式傳輸資料</span><span class="sxs-lookup"><span data-stu-id="0b0cb-236">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="0b0cb-237">使用 AzCopy 命令列公用程式 on Linux 傳送資料</span><span class="sxs-lookup"><span data-stu-id="0b0cb-237">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="0b0cb-238">設定 Azure 儲存體連接字串</span><span class="sxs-lookup"><span data-stu-id="0b0cb-238">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="0b0cb-239">Azure 儲存體團隊部落格</span><span class="sxs-lookup"><span data-stu-id="0b0cb-239">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
