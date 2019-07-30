---
title: 使用 F# 開始使用 Azure 檔案儲存體
description: 使用 Azure 檔案儲存體在雲端中儲存檔案資料, 並從 Azure 虛擬機器 (VM) 或從執行 Windows 的內部部署應用程式掛接雲端檔案共用。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: a0e3cab56ba0f3db27335822616b4976a5d9de62
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630502"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="eacc4-103">開始使用 F 來使用 Azure 檔案儲存體\#</span><span class="sxs-lookup"><span data-stu-id="eacc4-103">Get started with Azure File storage using F\#</span></span>

<span data-ttu-id="eacc4-104">Azure 檔案儲存體是一項服務, 可使用標準[伺服器訊息區 (SMB) 通訊協定](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx), 在雲端中提供檔案共用。</span><span class="sxs-lookup"><span data-stu-id="eacc4-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="eacc4-105">SMB 2.1 和 SMB 3.0 都受到支援。</span><span class="sxs-lookup"><span data-stu-id="eacc4-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="eacc4-106">使用 Azure 檔案儲存體, 您可以快速地將依賴檔案共用的繼承應用程式遷移至 Azure, 而不需要昂貴的重寫。</span><span class="sxs-lookup"><span data-stu-id="eacc4-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="eacc4-107">在 Azure 虛擬機器或雲端服務中或從內部部署用戶端執行的應用程式可以在雲端掛接檔案共用, 就像桌面應用程式裝載一般的 SMB 共用一樣。</span><span class="sxs-lookup"><span data-stu-id="eacc4-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="eacc4-108">然後, 任何數目的應用程式元件都可以同時掛接和存取檔案儲存體共用。</span><span class="sxs-lookup"><span data-stu-id="eacc4-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="eacc4-109">如需檔案儲存體的概念總覽, 請參閱[.net guide for file storage](/azure/storage/storage-dotnet-how-to-use-files)。</span><span class="sxs-lookup"><span data-stu-id="eacc4-109">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eacc4-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="eacc4-110">Prerequisites</span></span>

<span data-ttu-id="eacc4-111">若要使用本指南, 您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。</span><span class="sxs-lookup"><span data-stu-id="eacc4-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="eacc4-112">您也需要此帳戶的儲存體存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="eacc4-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="eacc4-113">建立F#腳本並啟動F#互動式</span><span class="sxs-lookup"><span data-stu-id="eacc4-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="eacc4-114">本文中的範例可用於F#應用程式或F#腳本中。</span><span class="sxs-lookup"><span data-stu-id="eacc4-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="eacc4-115">若要建立F#腳本, 請在`.fsx` F#開發環境中建立`files.fsx`副檔名為的檔案, 例如。</span><span class="sxs-lookup"><span data-stu-id="eacc4-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="eacc4-116">接下來, 使用[Paket](https://fsprojects.github.io/Paket/)或`WindowsAzure.Storage` [NuGet](https://www.nuget.org/)之類的[套件管理員](package-management.md), 在您的腳本中`WindowsAzure.Storage.dll`使用`#r`指示詞安裝封裝和參考。</span><span class="sxs-lookup"><span data-stu-id="eacc4-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="eacc4-117">新增命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="eacc4-117">Add namespace declarations</span></span>

<span data-ttu-id="eacc4-118">將下列`open`語句新增至檔案頂端`files.fsx` :</span><span class="sxs-lookup"><span data-stu-id="eacc4-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="eacc4-119">取得您的連接字串</span><span class="sxs-lookup"><span data-stu-id="eacc4-119">Get your connection string</span></span>

<span data-ttu-id="eacc4-120">在本教學課程中, 您將需要 Azure 儲存體連接字串。</span><span class="sxs-lookup"><span data-stu-id="eacc4-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="eacc4-121">如需連接字串的詳細資訊, 請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="eacc4-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="eacc4-122">在本教學課程中, 您將在腳本中輸入連接字串, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="eacc4-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="eacc4-123">不過, 這**不建議**用於實際的專案。</span><span class="sxs-lookup"><span data-stu-id="eacc4-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="eacc4-124">您的儲存體帳戶金鑰類似于儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="eacc4-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="eacc4-125">請務必小心保護您的儲存體帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="eacc4-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="eacc4-126">請避免將它散發給其他使用者、進行硬式編碼, 或將它儲存在其他人可以存取的純文字檔案中。</span><span class="sxs-lookup"><span data-stu-id="eacc4-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="eacc4-127">如果您認為金鑰可能遭到入侵, 您可以使用 Azure 入口網站重新產生金鑰。</span><span class="sxs-lookup"><span data-stu-id="eacc4-127">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="eacc4-128">對於實際的應用程式而言, 維護儲存體連接字串的最佳方式是在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="eacc4-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="eacc4-129">若要從設定檔提取連接字串, 您可以執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="eacc4-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="eacc4-130">使用 Azure Configuration Manager 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="eacc4-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="eacc4-131">您也可以使用 API (例如 .NET Framework 的`ConfigurationManager`類型)。</span><span class="sxs-lookup"><span data-stu-id="eacc4-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="eacc4-132">剖析連接字串</span><span class="sxs-lookup"><span data-stu-id="eacc4-132">Parse the connection string</span></span>

<span data-ttu-id="eacc4-133">若要剖析連接字串, 請使用:</span><span class="sxs-lookup"><span data-stu-id="eacc4-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="eacc4-134">這會`CloudStorageAccount`傳回。</span><span class="sxs-lookup"><span data-stu-id="eacc4-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="eacc4-135">建立檔案服務用戶端</span><span class="sxs-lookup"><span data-stu-id="eacc4-135">Create the File service client</span></span>

<span data-ttu-id="eacc4-136">此`CloudFileClient`類型可讓您以程式設計方式使用儲存在檔案儲存體中的檔案。</span><span class="sxs-lookup"><span data-stu-id="eacc4-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="eacc4-137">以下是建立服務用戶端的其中一種方式:</span><span class="sxs-lookup"><span data-stu-id="eacc4-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="eacc4-138">現在您已準備好撰寫程式碼, 以讀取資料, 並將資料寫入檔案儲存體。</span><span class="sxs-lookup"><span data-stu-id="eacc4-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="eacc4-139">建立檔案共用</span><span class="sxs-lookup"><span data-stu-id="eacc4-139">Create a file share</span></span>

<span data-ttu-id="eacc4-140">這個範例示範如何建立檔案共用 (如果尚未存在):</span><span class="sxs-lookup"><span data-stu-id="eacc4-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="eacc4-141">建立根目錄和子目錄</span><span class="sxs-lookup"><span data-stu-id="eacc4-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="eacc4-142">在這裡, 您會取得根目錄, 並取得根目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="eacc4-142">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="eacc4-143">如果兩者都不存在, 您可以建立兩者。</span><span class="sxs-lookup"><span data-stu-id="eacc4-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="eacc4-144">將文字上傳為檔案</span><span class="sxs-lookup"><span data-stu-id="eacc4-144">Upload text as a file</span></span>

<span data-ttu-id="eacc4-145">這個範例示範如何將文字上傳為檔案。</span><span class="sxs-lookup"><span data-stu-id="eacc4-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="eacc4-146">將檔下載至檔案的本機複本</span><span class="sxs-lookup"><span data-stu-id="eacc4-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="eacc4-147">在這裡, 您會下載剛建立的檔案, 並將內容附加至本機檔案。</span><span class="sxs-lookup"><span data-stu-id="eacc4-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="eacc4-148">設定檔案共用的大小上限</span><span class="sxs-lookup"><span data-stu-id="eacc4-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="eacc4-149">下列範例顯示如何檢查共用的目前使用量, 以及如何設定共用的配額。</span><span class="sxs-lookup"><span data-stu-id="eacc4-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="eacc4-150">`FetchAttributes`必須呼叫以填入共用的`Properties`, 並`SetProperties`將本機變更傳播至 Azure 檔案儲存體。</span><span class="sxs-lookup"><span data-stu-id="eacc4-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="eacc4-151">產生檔案或檔案共用的共用存取簽章</span><span class="sxs-lookup"><span data-stu-id="eacc4-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="eacc4-152">您可以為檔案共用或個別檔案產生共用存取簽章 (SAS)。</span><span class="sxs-lookup"><span data-stu-id="eacc4-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="eacc4-153">您也可以在檔案共用上建立共用存取原則, 以管理共用存取簽章。</span><span class="sxs-lookup"><span data-stu-id="eacc4-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="eacc4-154">建議建立共用存取原則, 因為它會提供一種方法來撤銷 SAS (如果它應該遭到入侵)。</span><span class="sxs-lookup"><span data-stu-id="eacc4-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="eacc4-155">在這裡, 您會在共用上建立共用存取原則, 然後使用該原則為共用中的檔案提供 SAS 的條件約束。</span><span class="sxs-lookup"><span data-stu-id="eacc4-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="eacc4-156">如需建立和使用共用存取簽章的詳細資訊, 請參閱[使用共用存取簽章 (sas)](/azure/storage/storage-dotnet-shared-access-signature-part-1)和透過[Blob 儲存體建立和使用 SAS](/azure/storage/storage-dotnet-shared-access-signature-part-2)。</span><span class="sxs-lookup"><span data-stu-id="eacc4-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="eacc4-157">複製檔案</span><span class="sxs-lookup"><span data-stu-id="eacc4-157">Copy files</span></span>

<span data-ttu-id="eacc4-158">您可以將檔案複製到另一個檔案或 blob, 或將 blob 複製到檔案。</span><span class="sxs-lookup"><span data-stu-id="eacc4-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="eacc4-159">如果您要將 blob 複製到檔案, 或將檔案複製到 blob, 您*必須*使用共用存取簽章 (SAS) 來驗證來源物件, 即使您是在相同的儲存體帳戶內進行複製也一樣。</span><span class="sxs-lookup"><span data-stu-id="eacc4-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="eacc4-160">將檔案複製到另一個檔案</span><span class="sxs-lookup"><span data-stu-id="eacc4-160">Copy a file to another file</span></span>

<span data-ttu-id="eacc4-161">在這裡, 您會將檔案複製到相同共用中的另一個檔案。</span><span class="sxs-lookup"><span data-stu-id="eacc4-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="eacc4-162">因為這項複製作業會在相同儲存體帳戶中的檔案之間複製, 所以您可以使用共用金鑰驗證來執行複製。</span><span class="sxs-lookup"><span data-stu-id="eacc4-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="eacc4-163">將檔案複製到 blob</span><span class="sxs-lookup"><span data-stu-id="eacc4-163">Copy a file to a blob</span></span>

<span data-ttu-id="eacc4-164">在這裡, 您會建立檔案, 並將它複製到相同儲存體帳戶內的 blob。</span><span class="sxs-lookup"><span data-stu-id="eacc4-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="eacc4-165">您會建立來源檔案的 SAS, 服務會在複製作業期間使用該檔案來驗證來源檔案的存取權。</span><span class="sxs-lookup"><span data-stu-id="eacc4-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="eacc4-166">您可以使用相同的方式將 blob 複製到檔案。</span><span class="sxs-lookup"><span data-stu-id="eacc4-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="eacc4-167">如果來源物件是 blob, 則請建立 SAS, 以在複製作業期間驗證該 blob 的存取權。</span><span class="sxs-lookup"><span data-stu-id="eacc4-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="eacc4-168">使用計量針對檔案儲存體進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="eacc4-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="eacc4-169">Azure 儲存體分析支援檔案儲存體的計量。</span><span class="sxs-lookup"><span data-stu-id="eacc4-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="eacc4-170">使用計量資料, 您可以追蹤要求並診斷問題。</span><span class="sxs-lookup"><span data-stu-id="eacc4-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="eacc4-171">您可以從[Azure 入口網站](https://portal.azure.com)啟用檔案儲存體的計量, 也可以從F#下列方式進行:</span><span class="sxs-lookup"><span data-stu-id="eacc4-171">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="eacc4-172">後續步驟</span><span class="sxs-lookup"><span data-stu-id="eacc4-172">Next steps</span></span>

<span data-ttu-id="eacc4-173">如需 Azure 檔案儲存體的詳細資訊, 請參閱下列連結。</span><span class="sxs-lookup"><span data-stu-id="eacc4-173">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="eacc4-174">概念性文章和影片</span><span class="sxs-lookup"><span data-stu-id="eacc4-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="eacc4-175">Azure 檔案儲存體儲存體: 適用于 Windows 和 Linux 的順暢雲端 SMB 檔案系統</span><span class="sxs-lookup"><span data-stu-id="eacc4-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="eacc4-176">如何搭配使用 Azure 檔案儲存體與 Linux</span><span class="sxs-lookup"><span data-stu-id="eacc4-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="eacc4-177">檔案儲存體的工具支援</span><span class="sxs-lookup"><span data-stu-id="eacc4-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="eacc4-178">搭配 Azure 儲存體使用 Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="eacc4-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="eacc4-179">如何搭配 Microsoft Azure 儲存體使用 AzCopy</span><span class="sxs-lookup"><span data-stu-id="eacc4-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="eacc4-180">搭配 Azure 儲存體使用 Azure CLI</span><span class="sxs-lookup"><span data-stu-id="eacc4-180">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="eacc4-181">參考資料</span><span class="sxs-lookup"><span data-stu-id="eacc4-181">Reference</span></span>

- [<span data-ttu-id="eacc4-182">適用于 .NET 的儲存體用戶端程式庫參考</span><span class="sxs-lookup"><span data-stu-id="eacc4-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="eacc4-183">檔案服務 REST API 參考</span><span class="sxs-lookup"><span data-stu-id="eacc4-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="eacc4-184">Blog 文章</span><span class="sxs-lookup"><span data-stu-id="eacc4-184">Blog posts</span></span>

- [<span data-ttu-id="eacc4-185">Azure 檔案儲存體現已正式推出</span><span class="sxs-lookup"><span data-stu-id="eacc4-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="eacc4-186">內部 Azure 檔案儲存體</span><span class="sxs-lookup"><span data-stu-id="eacc4-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="eacc4-187">Microsoft Azure 檔案服務簡介</span><span class="sxs-lookup"><span data-stu-id="eacc4-187">Introducing Microsoft Azure File Service</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [<span data-ttu-id="eacc4-188">將連接保存到 Microsoft Azure 檔案</span><span class="sxs-lookup"><span data-stu-id="eacc4-188">Persisting connections to Microsoft Azure Files</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
