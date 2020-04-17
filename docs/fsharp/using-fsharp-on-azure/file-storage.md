---
title: 使用 F# 開始使用 Azure 檔案儲存體
description: 使用 Azure 檔案儲存體在雲端中儲存檔案資料，並從 Azure 虛擬機器 (VM) 或執行 Windows 的內部部署應用程式掛接雲端檔案共用。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 2088442e05ba36b388a3324942ebbf8c7eb263dd
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607463"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="18d99-103">使用 F 開始使用 Azure 檔案儲存\#</span><span class="sxs-lookup"><span data-stu-id="18d99-103">Get started with Azure File storage using F\#</span></span>

<span data-ttu-id="18d99-104">Azure 檔案儲存是使用標準[伺服器訊息塊 (SMB) 協定](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)在雲端中提供檔案共享的服務。</span><span class="sxs-lookup"><span data-stu-id="18d99-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="18d99-105">SMB 2.1 和 SMB 3.0 皆受到支援。</span><span class="sxs-lookup"><span data-stu-id="18d99-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="18d99-106">使用 Azure 檔案儲存體時，您可以快速地將依賴檔案共用功能的舊式應用程式移轉至 Azure，而不必浪費成本來重新撰寫程式。</span><span class="sxs-lookup"><span data-stu-id="18d99-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="18d99-107">在 Azure 虛擬機器、雲端服務或內部部署中執行的應用程式，可掛接雲端中的檔案共用，就像桌面應用程式掛接一般 SMB 共用一樣。</span><span class="sxs-lookup"><span data-stu-id="18d99-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="18d99-108">可同時掛接和存取檔案儲存體共用的應用程式元件數量沒有限制。</span><span class="sxs-lookup"><span data-stu-id="18d99-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="18d99-109">有關檔案儲存的概念概述,請參閱[.NET 檔案儲存指南](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files)。</span><span class="sxs-lookup"><span data-stu-id="18d99-109">For a conceptual overview of file storage, please see [the .NET guide for file storage](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="18d99-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="18d99-110">Prerequisites</span></span>

<span data-ttu-id="18d99-111">要使用本指南,必須首先建立[Azure 儲存帳戶](https://docs.microsoft.com/azure/storage/storage-create-storage-account)。</span><span class="sxs-lookup"><span data-stu-id="18d99-111">To use this guide, you must first [create an Azure storage account](https://docs.microsoft.com/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="18d99-112">您還需要此帳戶的儲存存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="18d99-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="18d99-113">建立 F# 文稿與開始 F# 互動式</span><span class="sxs-lookup"><span data-stu-id="18d99-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="18d99-114">本文中的範例可用於 F# 應用程式或 F# 文稿。</span><span class="sxs-lookup"><span data-stu-id="18d99-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="18d99-115">要建立 F# 文稿,請建立`.fsx`一個 包含副`files.fsx`檔名的檔案 ,例如,在 F# 開發環境中。</span><span class="sxs-lookup"><span data-stu-id="18d99-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="18d99-116">接下來,使用[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)等`WindowsAzure.Storage``#r`[套件管理器](package-management.md)使用 指令在文稿`WindowsAzure.Storage.dll`中安裝包和引用。</span><span class="sxs-lookup"><span data-stu-id="18d99-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="18d99-117">新增命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="18d99-117">Add namespace declarations</span></span>

<span data-ttu-id="18d99-118">在 `files.fsx` 檔案頂端新增下列 `open` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="18d99-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="18d99-119">取得您的連接字串</span><span class="sxs-lookup"><span data-stu-id="18d99-119">Get your connection string</span></span>

<span data-ttu-id="18d99-120">本教程需要 Azure 儲存連接字串。</span><span class="sxs-lookup"><span data-stu-id="18d99-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="18d99-121">有關連接字串的詳細資訊,請參考[設定儲存連線字串](https://docs.microsoft.com/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="18d99-121">For more information about connection strings, see [Configure Storage Connection Strings](https://docs.microsoft.com/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="18d99-122">在本教學中,您將在文稿中輸入連接字串,如下所示:</span><span class="sxs-lookup"><span data-stu-id="18d99-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="18d99-123">但是,**不建議**對實際項目進行此類使用。</span><span class="sxs-lookup"><span data-stu-id="18d99-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="18d99-124">儲存體帳戶金鑰很類似儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="18d99-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="18d99-125">請務必小心保護您的儲存體帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="18d99-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="18d99-126">請避免轉發給其他使用者、進行硬式編碼，或將它儲存在其他人可以存取的純文字檔案。</span><span class="sxs-lookup"><span data-stu-id="18d99-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="18d99-127">如果您認為密鑰可能已洩露,則可以使用 Azure 門戶重新生成密鑰。</span><span class="sxs-lookup"><span data-stu-id="18d99-127">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="18d99-128">對於實際應用程式,維護存儲連接字串的最佳方法是在配置檔中。</span><span class="sxs-lookup"><span data-stu-id="18d99-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="18d99-129">要從設定檔中取得連接字串,可以執行以下操作:</span><span class="sxs-lookup"><span data-stu-id="18d99-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="18d99-130">是否使用 Azure Configuration Manager 可由您選擇。</span><span class="sxs-lookup"><span data-stu-id="18d99-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="18d99-131">您還可以使用 API,如 .NET`ConfigurationManager`框架的類型 。</span><span class="sxs-lookup"><span data-stu-id="18d99-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="18d99-132">解析連接字串</span><span class="sxs-lookup"><span data-stu-id="18d99-132">Parse the connection string</span></span>

<span data-ttu-id="18d99-133">要分析連接字串,請使用:</span><span class="sxs-lookup"><span data-stu-id="18d99-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="18d99-134">這會傳回`CloudStorageAccount`。</span><span class="sxs-lookup"><span data-stu-id="18d99-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="18d99-135">建立檔案服務用戶端</span><span class="sxs-lookup"><span data-stu-id="18d99-135">Create the File service client</span></span>

<span data-ttu-id="18d99-136">該`CloudFileClient`類型使您能夠以程式設計方式使用儲存在檔案儲存中的檔案。</span><span class="sxs-lookup"><span data-stu-id="18d99-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="18d99-137">以下是建立服務用戶端的其中一種方式：</span><span class="sxs-lookup"><span data-stu-id="18d99-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="18d99-138">現在,您可以編寫從檔案儲存讀取數據並將數據寫入檔案存儲的代碼。</span><span class="sxs-lookup"><span data-stu-id="18d99-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="18d99-139">建立檔案共用</span><span class="sxs-lookup"><span data-stu-id="18d99-139">Create a file share</span></span>

<span data-ttu-id="18d99-140">此範例展示如何建立檔案分享(如果檔案分享不存在):</span><span class="sxs-lookup"><span data-stu-id="18d99-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="18d99-141">建立根目錄與子目錄</span><span class="sxs-lookup"><span data-stu-id="18d99-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="18d99-142">在這裡,您將獲得根目錄,並獲得根的子目錄。</span><span class="sxs-lookup"><span data-stu-id="18d99-142">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="18d99-143">如果它們不存在,則建立兩者。</span><span class="sxs-lookup"><span data-stu-id="18d99-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="18d99-144">將文字作為檔案上載</span><span class="sxs-lookup"><span data-stu-id="18d99-144">Upload text as a file</span></span>

<span data-ttu-id="18d99-145">此示例演示如何將文本上傳為檔。</span><span class="sxs-lookup"><span data-stu-id="18d99-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="18d99-146">將檔案下載到檔案的本地複本</span><span class="sxs-lookup"><span data-stu-id="18d99-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="18d99-147">在這裡,您可以下載剛剛創建的檔,將內容追加到本地檔案中。</span><span class="sxs-lookup"><span data-stu-id="18d99-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="18d99-148">設定檔案共用的大小上限</span><span class="sxs-lookup"><span data-stu-id="18d99-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="18d99-149">下列範例示範如何檢查共用的目前使用狀況，以及如何設定共用的配額。</span><span class="sxs-lookup"><span data-stu-id="18d99-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="18d99-150">`FetchAttributes`必須呼叫 以填充共用`Properties`的`SetProperties`,並將本地更改傳播到 Azure 檔案儲存。</span><span class="sxs-lookup"><span data-stu-id="18d99-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="18d99-151">產生檔案或檔案共用的共用存取簽章</span><span class="sxs-lookup"><span data-stu-id="18d99-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="18d99-152">您可以為檔案共用或個別檔案產生共用存取簽章 (SAS)。</span><span class="sxs-lookup"><span data-stu-id="18d99-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="18d99-153">您也可以在檔案共用上建立共用存取原則，以管理共用存取簽章。</span><span class="sxs-lookup"><span data-stu-id="18d99-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="18d99-154">建議您建立共用存取原則，因為如果必須洩漏 SAS，它提供了一種撤銷 SAS 的方式。</span><span class="sxs-lookup"><span data-stu-id="18d99-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="18d99-155">在這裡,在共用上創建共享存取策略,然後使用該策略為共用中的檔上的 SAS 提供約束。</span><span class="sxs-lookup"><span data-stu-id="18d99-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="18d99-156">如需建立與使用共用存取簽章的詳細資訊，請參閱[共用存取簽章 (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1)和[透過 Blob 儲存體建立與使用 SAS](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-2)。</span><span class="sxs-lookup"><span data-stu-id="18d99-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="18d99-157">複製檔案</span><span class="sxs-lookup"><span data-stu-id="18d99-157">Copy files</span></span>

<span data-ttu-id="18d99-158">您可以將檔案複製到其他檔案或 Blob,或將 Blob 複製到檔案。</span><span class="sxs-lookup"><span data-stu-id="18d99-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="18d99-159">如果要將 Blob 複製到檔案或檔案複製到 Blob,*則必須*使用共享存取簽名 (SAS) 對來源物件進行身份驗證,即使您正在同一儲存帳戶複製也是如此。</span><span class="sxs-lookup"><span data-stu-id="18d99-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="18d99-160">將檔案複製到另一個檔案</span><span class="sxs-lookup"><span data-stu-id="18d99-160">Copy a file to another file</span></span>

<span data-ttu-id="18d99-161">在這裡,您將檔案複製到同一共用中的另一個檔。</span><span class="sxs-lookup"><span data-stu-id="18d99-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="18d99-162">由於此複製作業是在相同儲存體帳戶中的檔案間進行複製，所以您可以使用共用金鑰驗證執行複製。</span><span class="sxs-lookup"><span data-stu-id="18d99-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="18d99-163">將檔案複製到 Blob</span><span class="sxs-lookup"><span data-stu-id="18d99-163">Copy a file to a blob</span></span>

<span data-ttu-id="18d99-164">在這裡,您將創建一個檔並將其複製到同一存儲帳戶中的 Blob。</span><span class="sxs-lookup"><span data-stu-id="18d99-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="18d99-165">為源文件創建 SAS,服務用於在複製操作期間對源文件的訪問進行身份驗證。</span><span class="sxs-lookup"><span data-stu-id="18d99-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="18d99-166">您可以用相同方式將 Blob 複製到檔案。</span><span class="sxs-lookup"><span data-stu-id="18d99-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="18d99-167">如果來源物件為 Blob，則請建立 SAS，以便在複製作業期間驗證該 Blob 存取權。</span><span class="sxs-lookup"><span data-stu-id="18d99-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="18d99-168">使用度量疑難排解檔案儲存體</span><span class="sxs-lookup"><span data-stu-id="18d99-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="18d99-169">Azure 儲存分析支援檔案存儲的指標。</span><span class="sxs-lookup"><span data-stu-id="18d99-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="18d99-170">利用度量資料，您可以追蹤要求及診斷問題。</span><span class="sxs-lookup"><span data-stu-id="18d99-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="18d99-171">可以從[Azure 門戶](https://portal.azure.com)啟用檔案存儲的指標,也可以從 F# 執行此操作,如下所示:</span><span class="sxs-lookup"><span data-stu-id="18d99-171">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="18d99-172">後續步驟</span><span class="sxs-lookup"><span data-stu-id="18d99-172">Next steps</span></span>

<span data-ttu-id="18d99-173">請參閱這些連結以取得 Azure 檔案儲存體的相關詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="18d99-173">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="18d99-174">概念性文章和影片</span><span class="sxs-lookup"><span data-stu-id="18d99-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="18d99-175">Azure 檔案儲存體：適用於 Windows 和 Linux 的無摩擦雲端 SMB 檔案系統</span><span class="sxs-lookup"><span data-stu-id="18d99-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="18d99-176">如何使用 Azure 檔案儲存與 Linux</span><span class="sxs-lookup"><span data-stu-id="18d99-176">How to use Azure File Storage with Linux</span></span>](https://docs.microsoft.com/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="18d99-177">檔案儲存體的工具支援</span><span class="sxs-lookup"><span data-stu-id="18d99-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="18d99-178">搭配使用 Azure PowerShell 與 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="18d99-178">Using Azure PowerShell with Azure Storage</span></span>](https://docs.microsoft.com/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="18d99-179">如何搭配使用 AzCopy 與 Microsoft Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="18d99-179">How to use AzCopy with Microsoft Azure Storage</span></span>](https://docs.microsoft.com/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="18d99-180">使用 Azure CLI 上傳、下載及列出 Blob</span><span class="sxs-lookup"><span data-stu-id="18d99-180">Create, download, and list blobs with Azure CLI</span></span>](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="18d99-181">參考</span><span class="sxs-lookup"><span data-stu-id="18d99-181">Reference</span></span>

- [<span data-ttu-id="18d99-182">Storage Client Library for .NET 參考資料</span><span class="sxs-lookup"><span data-stu-id="18d99-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="18d99-183">檔案服務 REST API 參考</span><span class="sxs-lookup"><span data-stu-id="18d99-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="18d99-184">部落格文章</span><span class="sxs-lookup"><span data-stu-id="18d99-184">Blog posts</span></span>

- [<span data-ttu-id="18d99-185">Azure 檔案儲存體現已公開推出</span><span class="sxs-lookup"><span data-stu-id="18d99-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="18d99-186">在 Azure 檔案儲存中</span><span class="sxs-lookup"><span data-stu-id="18d99-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [<span data-ttu-id="18d99-187">Microsoft Azure 檔案服務簡介</span><span class="sxs-lookup"><span data-stu-id="18d99-187">Introducing Microsoft Azure File Service</span></span>](https://docs.microsoft.com/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [<span data-ttu-id="18d99-188">保留與 Microsoft Azure 檔案的連線</span><span class="sxs-lookup"><span data-stu-id="18d99-188">Persisting connections to Microsoft Azure Files</span></span>](https://docs.microsoft.com/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
