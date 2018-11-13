---
title: 開始使用 F# 的 Azure 檔案儲存體
description: 使用 Azure 檔案儲存體，在雲端中儲存檔案資料和從 Azure 虛擬機器 (VM) 掛接雲端檔案共用，或從內部部署應用程式執行 Windows。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: e772da5f81d2e6827295d0dfe150934a415eb3bb
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "33569339"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="b6446-103">開始使用 F# 的 Azure 檔案儲存體</span><span class="sxs-lookup"><span data-stu-id="b6446-103">Get started with Azure File storage using F#</span></span> #

<span data-ttu-id="b6446-104">Azure 檔案儲存體是一項服務，提供在雲端中使用標準的檔案共用[伺服器訊息區塊 (SMB) 通訊協定](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b6446-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="b6446-105">支援 SMB 2.1 和 SMB 3.0。</span><span class="sxs-lookup"><span data-stu-id="b6446-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="b6446-106">使用 Azure 檔案儲存體，您可以移轉舊版應用程式需要在 azure 檔案共用，快速且沒有成本高昂的重寫。</span><span class="sxs-lookup"><span data-stu-id="b6446-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="b6446-107">在 Azure 虛擬機器或雲端服務，或從內部部署用戶端執行的應用程式可以掛接雲端中的檔案共用，就像桌面應用程式掛接一般 SMB 共用。</span><span class="sxs-lookup"><span data-stu-id="b6446-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="b6446-108">任意數目的應用程式元件，然後掛接及同時存取檔案儲存體共用。</span><span class="sxs-lookup"><span data-stu-id="b6446-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="b6446-109">檔案儲存體概念的概觀，請參閱[檔案儲存體的.NET 指南](/azure/storage/storage-dotnet-how-to-use-files)。</span><span class="sxs-lookup"><span data-stu-id="b6446-109">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6446-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="b6446-110">Prerequisites</span></span>

<span data-ttu-id="b6446-111">若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。</span><span class="sxs-lookup"><span data-stu-id="b6446-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="b6446-112">儲存體存取金鑰也需要此帳戶。</span><span class="sxs-lookup"><span data-stu-id="b6446-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="b6446-113">建立 F# 指令碼，並開始 F# Interactive</span><span class="sxs-lookup"><span data-stu-id="b6446-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="b6446-114">這篇文章中的範例可以用於 F# 應用程式或 F# 指令碼。</span><span class="sxs-lookup"><span data-stu-id="b6446-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="b6446-115">若要建立 F# 指令碼，建立的檔案`.fsx`擴充功能，例如`files.fsx`，F# 開發環境中。</span><span class="sxs-lookup"><span data-stu-id="b6446-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="b6446-116">接下來，使用[套件管理員](package-management.md)這類[Paket](https://fsprojects.github.io/Paket/)或是[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`封裝和參考`WindowsAzure.Storage.dll`使用指令碼中`#r`指示詞。</span><span class="sxs-lookup"><span data-stu-id="b6446-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="b6446-117">加入命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="b6446-117">Add namespace declarations</span></span>

<span data-ttu-id="b6446-118">新增下列`open`陳述式的`files.fsx`檔案：</span><span class="sxs-lookup"><span data-stu-id="b6446-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="b6446-119">取得連接字串</span><span class="sxs-lookup"><span data-stu-id="b6446-119">Get your connection string</span></span>

<span data-ttu-id="b6446-120">在本教學課程需要 Azure 儲存體連接字串。</span><span class="sxs-lookup"><span data-stu-id="b6446-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="b6446-121">如需有關連接字串的詳細資訊，請參閱 <<c0> [ 設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="b6446-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="b6446-122">教學課程中，您會輸入您的連接字串中您的指令碼，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="b6446-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="b6446-123">不過，這是**不建議使用**實際的專案。</span><span class="sxs-lookup"><span data-stu-id="b6446-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="b6446-124">儲存體帳戶金鑰很類似儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="b6446-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="b6446-125">請務必小心保護您的儲存體帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="b6446-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="b6446-126">請避免轉發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。</span><span class="sxs-lookup"><span data-stu-id="b6446-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="b6446-127">您可以重新產生您使用 Azure 入口網站，如果您認為可能已遭盜用的金鑰。</span><span class="sxs-lookup"><span data-stu-id="b6446-127">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="b6446-128">實際的應用程式，來維護您的儲存體連接字串的最佳方式是在組態檔中。</span><span class="sxs-lookup"><span data-stu-id="b6446-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="b6446-129">若要從組態檔擷取連接字串，您可以這樣做：</span><span class="sxs-lookup"><span data-stu-id="b6446-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="b6446-130">使用 Azure Configuration Manager 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="b6446-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="b6446-131">您也可以使用 API，例如.NET Framework 的`ConfigurationManager`型別。</span><span class="sxs-lookup"><span data-stu-id="b6446-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="b6446-132">剖析連接字串</span><span class="sxs-lookup"><span data-stu-id="b6446-132">Parse the connection string</span></span>

<span data-ttu-id="b6446-133">若要剖析的連接字串，請使用：</span><span class="sxs-lookup"><span data-stu-id="b6446-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="b6446-134">這會傳回`CloudStorageAccount`。</span><span class="sxs-lookup"><span data-stu-id="b6446-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="b6446-135">建立檔案服務用戶端</span><span class="sxs-lookup"><span data-stu-id="b6446-135">Create the File service client</span></span>

<span data-ttu-id="b6446-136">`CloudFileClient`類型可讓您以程式設計方式使用檔案儲存體中儲存的檔案。</span><span class="sxs-lookup"><span data-stu-id="b6446-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="b6446-137">若要建立服務用戶端的其中一個方法如下：</span><span class="sxs-lookup"><span data-stu-id="b6446-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="b6446-138">現在您已準備好撰寫程式碼來讀取資料，並將資料寫入至檔案儲存體。</span><span class="sxs-lookup"><span data-stu-id="b6446-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="b6446-139">建立檔案共用</span><span class="sxs-lookup"><span data-stu-id="b6446-139">Create a file share</span></span>

<span data-ttu-id="b6446-140">此範例示範如何建立檔案共用，如果不存在：</span><span class="sxs-lookup"><span data-stu-id="b6446-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="b6446-141">建立根目錄和子目錄</span><span class="sxs-lookup"><span data-stu-id="b6446-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="b6446-142">在這裡，您可以目錄的根目錄，並取得子目錄的根目錄。</span><span class="sxs-lookup"><span data-stu-id="b6446-142">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="b6446-143">如果您建立兩者已不存在。</span><span class="sxs-lookup"><span data-stu-id="b6446-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="b6446-144">將文字上載檔案</span><span class="sxs-lookup"><span data-stu-id="b6446-144">Upload text as a file</span></span>

<span data-ttu-id="b6446-145">此範例示範如何上傳做為檔案的文字。</span><span class="sxs-lookup"><span data-stu-id="b6446-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="b6446-146">將檔案下載至本機檔案的複本</span><span class="sxs-lookup"><span data-stu-id="b6446-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="b6446-147">您在此下載剛才建立的檔案附加到本機檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="b6446-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="b6446-148">設定檔案共用的大小上限</span><span class="sxs-lookup"><span data-stu-id="b6446-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="b6446-149">下列範例會示範如何檢查共用的目前使用量以及如何設定共用的配額。</span><span class="sxs-lookup"><span data-stu-id="b6446-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="b6446-150">`FetchAttributes` 必須先呼叫來填入共用`Properties`，和`SetProperties`將本機變更傳播至 Azure 檔案儲存體。</span><span class="sxs-lookup"><span data-stu-id="b6446-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="b6446-151">產生的檔案或檔案共用的共用的存取簽章</span><span class="sxs-lookup"><span data-stu-id="b6446-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="b6446-152">您可以產生共用的存取簽章 (SAS) 的檔案共用或個別的檔案。</span><span class="sxs-lookup"><span data-stu-id="b6446-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="b6446-153">您也可以建立共用的存取原則來管理共用的存取簽章的檔案共用上。</span><span class="sxs-lookup"><span data-stu-id="b6446-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="b6446-154">建立共用的存取原則建議，因為它提供一種撤銷 SAS，如果必須洩漏。</span><span class="sxs-lookup"><span data-stu-id="b6446-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="b6446-155">在這裡，您建立共用存取原則上的共用，然後使用該原則上的檔案共用中的 sas 提供條件約束。</span><span class="sxs-lookup"><span data-stu-id="b6446-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="b6446-156">如需有關建立和使用共用的存取簽章的詳細資訊，請參閱 <<c0> [ 使用共用存取簽章 (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1)並[建立及使用具有 Blob 儲存體的 SAS](/azure/storage/storage-dotnet-shared-access-signature-part-2)。</span><span class="sxs-lookup"><span data-stu-id="b6446-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="b6446-157">將檔案複製</span><span class="sxs-lookup"><span data-stu-id="b6446-157">Copy files</span></span>

<span data-ttu-id="b6446-158">您可以將檔案複製到另一個檔案或 blob 或 blob 檔案。</span><span class="sxs-lookup"><span data-stu-id="b6446-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="b6446-159">如果您將 blob 複製到檔案或檔案的 blob，您*必須*使用共用的存取簽章 (SAS) 驗證來源物件，即使您要複製相同的儲存體帳戶內。</span><span class="sxs-lookup"><span data-stu-id="b6446-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="b6446-160">將檔案複製到另一個檔案</span><span class="sxs-lookup"><span data-stu-id="b6446-160">Copy a file to another file</span></span>

<span data-ttu-id="b6446-161">在這裡，您將檔案複製到相同共用中的另一個檔案。</span><span class="sxs-lookup"><span data-stu-id="b6446-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="b6446-162">因為此複製作業在相同的儲存體帳戶中的檔案間進行複製，您可以使用共用金鑰驗證來執行複製。</span><span class="sxs-lookup"><span data-stu-id="b6446-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="b6446-163">將檔案複製到 blob</span><span class="sxs-lookup"><span data-stu-id="b6446-163">Copy a file to a blob</span></span>

<span data-ttu-id="b6446-164">在這裡，您會建立檔案並將它複製到相同的儲存體帳戶內的 blob。</span><span class="sxs-lookup"><span data-stu-id="b6446-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="b6446-165">您建立原始程式檔，供服務用來在複製作業期間驗證來源檔案的權限的 SAS。</span><span class="sxs-lookup"><span data-stu-id="b6446-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="b6446-166">您可以相同的方式，將 blob 複製到檔案中。</span><span class="sxs-lookup"><span data-stu-id="b6446-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="b6446-167">如果來源物件是 blob，請建立 SAS，以便在複製作業期間驗證該 blob 的存取權。</span><span class="sxs-lookup"><span data-stu-id="b6446-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="b6446-168">使用度量疑難排解檔案儲存體</span><span class="sxs-lookup"><span data-stu-id="b6446-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="b6446-169">Azure 儲存體分析可支援檔案儲存體的度量。</span><span class="sxs-lookup"><span data-stu-id="b6446-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="b6446-170">利用度量資料，您可以追蹤要求，並診斷問題。</span><span class="sxs-lookup"><span data-stu-id="b6446-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="b6446-171">您可以從檔案儲存體度量[Azure 入口網站](https://portal.azure.com)，或者，您可以從F#如下所示：</span><span class="sxs-lookup"><span data-stu-id="b6446-171">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="b6446-172">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b6446-172">Next steps</span></span>

<span data-ttu-id="b6446-173">請參閱下列連結以取得 Azure 檔案儲存體的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b6446-173">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="b6446-174">概念性文章和影片</span><span class="sxs-lookup"><span data-stu-id="b6446-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="b6446-175">Azure 檔案儲存體： 無摩擦雲端 SMB 檔案系統的 Windows 和 Linux</span><span class="sxs-lookup"><span data-stu-id="b6446-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="b6446-176">如何搭配 Linux 使用 Azure 檔案儲存體</span><span class="sxs-lookup"><span data-stu-id="b6446-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="b6446-177">檔案儲存體的工具支援</span><span class="sxs-lookup"><span data-stu-id="b6446-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="b6446-178">使用 Azure PowerShell 與 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="b6446-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="b6446-179">如何使用 AzCopy 與 Microsoft Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="b6446-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="b6446-180">使用 Azure CLI 搭配 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="b6446-180">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="b6446-181">參考資料</span><span class="sxs-lookup"><span data-stu-id="b6446-181">Reference</span></span>

- [<span data-ttu-id="b6446-182">For.NET 參考資料的儲存體用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="b6446-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="b6446-183">檔案服務 REST API 參考</span><span class="sxs-lookup"><span data-stu-id="b6446-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="b6446-184">部落格文章</span><span class="sxs-lookup"><span data-stu-id="b6446-184">Blog posts</span></span>

- [<span data-ttu-id="b6446-185">Azure 檔案儲存體現已正式推出</span><span class="sxs-lookup"><span data-stu-id="b6446-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="b6446-186">深入探討 Azure 檔案儲存體</span><span class="sxs-lookup"><span data-stu-id="b6446-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="b6446-187">Microsoft Azure 檔案服務簡介</span><span class="sxs-lookup"><span data-stu-id="b6446-187">Introducing Microsoft Azure File Service</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [<span data-ttu-id="b6446-188">保留與 Microsoft Azure 檔案連線</span><span class="sxs-lookup"><span data-stu-id="b6446-188">Persisting connections to Microsoft Azure Files</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
