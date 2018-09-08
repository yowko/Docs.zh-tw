---
title: WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 7c9b713571cea3d2c8c5f6511f2cfab7e87b80ee
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189273"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a><span data-ttu-id="ba3ae-102">WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="ba3ae-102">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>

<span data-ttu-id="ba3ae-103">DataSvcUtil.exe 是命令列工具所使用的 WCF Data Services 提供[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]摘要，並產生從.NET Framework 用戶端應用程式存取資料服務所需的用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-103">DataSvcUtil.exe is a command-line tool provided by WCF Data Services that consumes an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed and generates the client data service classes that are needed to access a data service from a .NET Framework client application.</span></span> <span data-ttu-id="ba3ae-104">此公用程式可以透過使用下列中繼資料來源產生資料類別：</span><span class="sxs-lookup"><span data-stu-id="ba3ae-104">This utility can generate data classes by using the following metadata sources:</span></span>

-   <span data-ttu-id="ba3ae-105">資料服務的根 URI。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-105">The root URI of a data service.</span></span> <span data-ttu-id="ba3ae-106">此公用程式會要求服務中繼資料文件，以描述資料服務所公開的資料模型。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-106">The utility requests the service metadata document, which describes the data model exposed by the data service.</span></span> <span data-ttu-id="ba3ae-107">如需詳細資訊，請參閱 < [OData： 服務中繼資料文件](https://go.microsoft.com/fwlink/?LinkId=186070)。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-107">For more information, see [OData: Service Metadata Document](https://go.microsoft.com/fwlink/?LinkId=186070).</span></span>

-   <span data-ttu-id="ba3ae-108">定義使用概念結構定義語言 (CSDL) 中所定義的資料模型檔案 (.csdl) [ \[MC-CSDL\]： 概念結構定義檔案格式](https://go.microsoft.com/fwlink/?LinkID=159072)規格。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-108">A data model file (.csdl) defined by using the conceptual schema definition language (CSDL), as defined in the [\[MC-CSDL\]: Conceptual Schema Definition File Format](https://go.microsoft.com/fwlink/?LinkID=159072) specification.</span></span>

-   <span data-ttu-id="ba3ae-109">使用 Entity Framework 提供之實體資料模型所建立的 .edmx 檔案。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-109">An .edmx file created by using the Entity Data Model tools that are provided with the Entity Framework.</span></span> <span data-ttu-id="ba3ae-110">如需詳細資訊，請參閱 < [ \[MC-EDMX\]： 資料服務封裝格式的實體資料模型](https://go.microsoft.com/fwlink/?LinkID=178833)規格。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-110">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) specification.</span></span>

<span data-ttu-id="ba3ae-111">如需詳細資訊，請參閱 <<c0> [ 如何： 手動產生用戶端資料服務類別](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-111">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>

<span data-ttu-id="ba3ae-112">DataSvcUtil.exe 工具安裝在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 目錄中。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-112">The DataSvcUtil.exe tool is installed in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory.</span></span> <span data-ttu-id="ba3ae-113">在許多情況下，這位於*C:\Windows\Microsoft.NET\Framework\v4.0*。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-113">In many cases, this is located in *C:\Windows\Microsoft.NET\Framework\v4.0*.</span></span> <span data-ttu-id="ba3ae-114">適用於 64 位元系統，這位於*C:\Windows\Microsoft.NET\Framework64\v4.0*。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-114">For 64-bit systems, this is located in *C:\Windows\Microsoft.NET\Framework64\v4.0*.</span></span> <span data-ttu-id="ba3ae-115">您也可以存取 DataSvcUtil.exe 工具從開發人員命令提示字元適用於 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-115">You can also access the DataSvcUtil.exe tool from Developer Command Prompt for Visual Studio.</span></span>

## <a name="syntax"></a><span data-ttu-id="ba3ae-116">語法</span><span class="sxs-lookup"><span data-stu-id="ba3ae-116">Syntax</span></span>

```
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

### <a name="parameters"></a><span data-ttu-id="ba3ae-117">參數</span><span class="sxs-lookup"><span data-stu-id="ba3ae-117">Parameters</span></span>

|<span data-ttu-id="ba3ae-118">選項</span><span class="sxs-lookup"><span data-stu-id="ba3ae-118">Option</span></span>|<span data-ttu-id="ba3ae-119">描述</span><span class="sxs-lookup"><span data-stu-id="ba3ae-119">Description</span></span>|
|------------|-----------------|
|`/dataservicecollection`|<span data-ttu-id="ba3ae-120">指定同時產生將物件繫結至控制項所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-120">Specifies that the code required to bind objects to controls is also generated.</span></span>|
|`/help`<br /><br /> <span data-ttu-id="ba3ae-121">-或-</span><span class="sxs-lookup"><span data-stu-id="ba3ae-121">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="ba3ae-122">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-122">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="ba3ae-123">`/in:` *\<檔案 >*</span><span class="sxs-lookup"><span data-stu-id="ba3ae-123">`/in:` *\<file>*</span></span>|<span data-ttu-id="ba3ae-124">指定 .csdl 或 .edmx 檔案，或是檔案所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-124">Specifies the .csdl or .edmx file or a directory where the file is located.</span></span>|
|<span data-ttu-id="ba3ae-125">`/language:`[VB&#124;CSharp]</span><span class="sxs-lookup"><span data-stu-id="ba3ae-125">`/language:`[VB&#124;CSharp]</span></span>|<span data-ttu-id="ba3ae-126">指定所產生之原始程式碼檔案的語言。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-126">Specifies the language for the generated source code files.</span></span> <span data-ttu-id="ba3ae-127">預設語言為 C#。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-127">The language defaults to C#.</span></span>|
|`/nologo`|<span data-ttu-id="ba3ae-128">隱藏著作權訊息。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-128">Suppresses the copyright message from displaying.</span></span>|
|<span data-ttu-id="ba3ae-129">`/out:` *\<檔案 >*</span><span class="sxs-lookup"><span data-stu-id="ba3ae-129">`/out:` *\<file>*</span></span>|<span data-ttu-id="ba3ae-130">指定原始程式碼檔案的名稱，該檔案包含已產生的用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-130">Specifies the name of the source code file that contains the generated client data service classes.</span></span>|
|<span data-ttu-id="ba3ae-131">`/uri:` *\<字串 >*</span><span class="sxs-lookup"><span data-stu-id="ba3ae-131">`/uri:` *\<string>*</span></span>|<span data-ttu-id="ba3ae-132">OData 摘要的 URI。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-132">The URI of the OData feed.</span></span>|
|<span data-ttu-id="ba3ae-133">`/version:`[1.0&#124;2.0]</span><span class="sxs-lookup"><span data-stu-id="ba3ae-133">`/version:`[1.0&#124;2.0]</span></span>|<span data-ttu-id="ba3ae-134">指定 OData 的最高接受的版本。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-134">Specifies the highest accepted version of OData.</span></span> <span data-ttu-id="ba3ae-135">版本取決於`DataServiceVersion`DataService 中項目的屬性傳回的資料服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-135">The version is determined based on the `DataServiceVersion` attribute of the DataService element in the returned data service metadata.</span></span> <span data-ttu-id="ba3ae-136">如需詳細資訊，請參閱 <<c0> [ 資料服務版本控制](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-136">For more information, see [Data Service Versioning](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).</span></span> <span data-ttu-id="ba3ae-137">當您指定`/dataservicecollection`參數，您也必須指定`/version:2.0`以啟用資料繫結。</span><span class="sxs-lookup"><span data-stu-id="ba3ae-137">When you specify the `/dataservicecollection` parameter, you must also specify `/version:2.0` to enable data binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ba3ae-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba3ae-138">See Also</span></span>

- [<span data-ttu-id="ba3ae-139">產生資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="ba3ae-139">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="ba3ae-140">如何：新增資料服務參考</span><span class="sxs-lookup"><span data-stu-id="ba3ae-140">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
