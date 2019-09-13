---
title: WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 7632362339cf9e23599f4f688f98cbc1d0b32114
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894244"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a><span data-ttu-id="f2c46-102">WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="f2c46-102">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>

<span data-ttu-id="f2c46-103">DataSvcUtil 是 WCF Data Services 所提供的命令列工具，它[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]會取用摘要，並產生從 .NET Framework 用戶端應用程式存取資料服務所需的用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="f2c46-103">DataSvcUtil.exe is a command-line tool provided by WCF Data Services that consumes an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed and generates the client data service classes that are needed to access a data service from a .NET Framework client application.</span></span> <span data-ttu-id="f2c46-104">此公用程式可以透過使用下列中繼資料來源產生資料類別：</span><span class="sxs-lookup"><span data-stu-id="f2c46-104">This utility can generate data classes by using the following metadata sources:</span></span>

- <span data-ttu-id="f2c46-105">資料服務的根 URI。</span><span class="sxs-lookup"><span data-stu-id="f2c46-105">The root URI of a data service.</span></span> <span data-ttu-id="f2c46-106">此公用程式會要求服務中繼資料文件，以描述資料服務所公開的資料模型。</span><span class="sxs-lookup"><span data-stu-id="f2c46-106">The utility requests the service metadata document, which describes the data model exposed by the data service.</span></span> <span data-ttu-id="f2c46-107">如需詳細資訊， [請參閱 OData：服務中繼資料](https://go.microsoft.com/fwlink/?LinkId=186070)檔。</span><span class="sxs-lookup"><span data-stu-id="f2c46-107">For more information, see [OData: Service Metadata Document](https://go.microsoft.com/fwlink/?LinkId=186070).</span></span>

- <span data-ttu-id="f2c46-108">使用概念結構定義語言（csdl）定義的資料模型檔案（csdl），如 MC-csdl [ \]中所\[定義：概念架構定義檔案格式](https://go.microsoft.com/fwlink/?LinkID=159072)規格。</span><span class="sxs-lookup"><span data-stu-id="f2c46-108">A data model file (.csdl) defined by using the conceptual schema definition language (CSDL), as defined in the [\[MC-CSDL\]: Conceptual Schema Definition File Format](https://go.microsoft.com/fwlink/?LinkID=159072) specification.</span></span>

- <span data-ttu-id="f2c46-109">使用 Entity Framework 提供之實體資料模型所建立的 .edmx 檔案。</span><span class="sxs-lookup"><span data-stu-id="f2c46-109">An .edmx file created by using the Entity Data Model tools that are provided with the Entity Framework.</span></span> <span data-ttu-id="f2c46-110">如需詳細資訊，請[參閱\[MC-\]EDMX：資料服務封裝格式](https://go.microsoft.com/fwlink/?LinkID=178833)規格的實體資料模型。</span><span class="sxs-lookup"><span data-stu-id="f2c46-110">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) specification.</span></span>

<span data-ttu-id="f2c46-111">如需詳細資訊，請參閱[如何：手動產生用戶端資料服務](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)類別。</span><span class="sxs-lookup"><span data-stu-id="f2c46-111">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>

<span data-ttu-id="f2c46-112">DataSvcUtil 工具會安裝在 .NET Framework 目錄中。</span><span class="sxs-lookup"><span data-stu-id="f2c46-112">The DataSvcUtil.exe tool is installed in the .NET Framework directory.</span></span> <span data-ttu-id="f2c46-113">在許多情況下，這是位於*c:\windows\microsoft.net\framework\v4.0 加入*中。</span><span class="sxs-lookup"><span data-stu-id="f2c46-113">In many cases, this is located in *C:\Windows\Microsoft.NET\Framework\v4.0*.</span></span> <span data-ttu-id="f2c46-114">若是64位系統，這會位於*C:\Windows\Microsoft.NET\Framework64\v4.0*中。</span><span class="sxs-lookup"><span data-stu-id="f2c46-114">For 64-bit systems, this is located in *C:\Windows\Microsoft.NET\Framework64\v4.0*.</span></span> <span data-ttu-id="f2c46-115">您也可以從 Visual Studio 的開發人員命令提示字元存取 DataSvcUtil 工具。</span><span class="sxs-lookup"><span data-stu-id="f2c46-115">You can also access the DataSvcUtil.exe tool from Developer Command Prompt for Visual Studio.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2c46-116">語法</span><span class="sxs-lookup"><span data-stu-id="f2c46-116">Syntax</span></span>

```console
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a><span data-ttu-id="f2c46-117">參數</span><span class="sxs-lookup"><span data-stu-id="f2c46-117">Parameters</span></span>

|<span data-ttu-id="f2c46-118">選項</span><span class="sxs-lookup"><span data-stu-id="f2c46-118">Option</span></span>|<span data-ttu-id="f2c46-119">說明</span><span class="sxs-lookup"><span data-stu-id="f2c46-119">Description</span></span>|
|------------|-----------------|
|`/dataservicecollection`|<span data-ttu-id="f2c46-120">指定同時產生將物件繫結至控制項所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f2c46-120">Specifies that the code required to bind objects to controls is also generated.</span></span>|
|`/help`<br /><br /> <span data-ttu-id="f2c46-121">-或-</span><span class="sxs-lookup"><span data-stu-id="f2c46-121">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="f2c46-122">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="f2c46-122">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="f2c46-123">`/in:`檔案 >  *\<*</span><span class="sxs-lookup"><span data-stu-id="f2c46-123">`/in:` *\<file>*</span></span>|<span data-ttu-id="f2c46-124">指定 .csdl 或 .edmx 檔案，或是檔案所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="f2c46-124">Specifies the .csdl or .edmx file or a directory where the file is located.</span></span>|
|<span data-ttu-id="f2c46-125">`/language:`[VB&#124;CSharp]</span><span class="sxs-lookup"><span data-stu-id="f2c46-125">`/language:`[VB&#124;CSharp]</span></span>|<span data-ttu-id="f2c46-126">指定所產生之原始程式碼檔案的語言。</span><span class="sxs-lookup"><span data-stu-id="f2c46-126">Specifies the language for the generated source code files.</span></span> <span data-ttu-id="f2c46-127">預設語言為 C#。</span><span class="sxs-lookup"><span data-stu-id="f2c46-127">The language defaults to C#.</span></span>|
|`/nologo`|<span data-ttu-id="f2c46-128">隱藏著作權訊息。</span><span class="sxs-lookup"><span data-stu-id="f2c46-128">Suppresses the copyright message from displaying.</span></span>|
|<span data-ttu-id="f2c46-129">`/out:`檔案 >  *\<*</span><span class="sxs-lookup"><span data-stu-id="f2c46-129">`/out:` *\<file>*</span></span>|<span data-ttu-id="f2c46-130">指定原始程式碼檔案的名稱，該檔案包含已產生的用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="f2c46-130">Specifies the name of the source code file that contains the generated client data service classes.</span></span>|
|<span data-ttu-id="f2c46-131">`/uri:`*字串\<>*</span><span class="sxs-lookup"><span data-stu-id="f2c46-131">`/uri:` *\<string>*</span></span>|<span data-ttu-id="f2c46-132">OData 摘要的 URI。</span><span class="sxs-lookup"><span data-stu-id="f2c46-132">The URI of the OData feed.</span></span>|
|<span data-ttu-id="f2c46-133">`/version:`[1.0&#124;2.0]</span><span class="sxs-lookup"><span data-stu-id="f2c46-133">`/version:`[1.0&#124;2.0]</span></span>|<span data-ttu-id="f2c46-134">指定最高的 OData 已接受版本。</span><span class="sxs-lookup"><span data-stu-id="f2c46-134">Specifies the highest accepted version of OData.</span></span> <span data-ttu-id="f2c46-135">版本是根據`DataServiceVersion`傳回的資料服務中繼資料中 DataService 元素的屬性來決定。</span><span class="sxs-lookup"><span data-stu-id="f2c46-135">The version is determined based on the `DataServiceVersion` attribute of the DataService element in the returned data service metadata.</span></span> <span data-ttu-id="f2c46-136">如需詳細資訊，請參閱[資料服務版本](data-service-versioning-wcf-data-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="f2c46-136">For more information, see [Data Service Versioning](data-service-versioning-wcf-data-services.md).</span></span> <span data-ttu-id="f2c46-137">當您指定`/dataservicecollection`參數時，您也必須指定`/version:2.0`以啟用資料系結。</span><span class="sxs-lookup"><span data-stu-id="f2c46-137">When you specify the `/dataservicecollection` parameter, you must also specify `/version:2.0` to enable data binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="f2c46-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2c46-138">See also</span></span>

- [<span data-ttu-id="f2c46-139">產生資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="f2c46-139">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="f2c46-140">如何：加入資料服務參考</span><span class="sxs-lookup"><span data-stu-id="f2c46-140">How to: Add a Data Service Reference</span></span>](how-to-add-a-data-service-reference-wcf-data-services.md)
