---
title: WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: de260e1a6b58fdbac1a2f0f40c7ec2e50b13644e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975091"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a><span data-ttu-id="1d524-102">WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="1d524-102">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>

<span data-ttu-id="1d524-103">DataSvcUtil 是 WCF Data Services 所提供的命令列工具，它會使用開放式資料通訊協定（OData）摘要，並產生從 .NET Framework 用戶端應用程式存取資料服務所需的用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="1d524-103">DataSvcUtil.exe is a command-line tool provided by WCF Data Services that consumes an Open Data Protocol (OData) feed and generates the client data service classes that are needed to access a data service from a .NET Framework client application.</span></span> <span data-ttu-id="1d524-104">此公用程式可以透過使用下列中繼資料來源產生資料類別：</span><span class="sxs-lookup"><span data-stu-id="1d524-104">This utility can generate data classes by using the following metadata sources:</span></span>

- <span data-ttu-id="1d524-105">資料服務的根 URI。</span><span class="sxs-lookup"><span data-stu-id="1d524-105">The root URI of a data service.</span></span> <span data-ttu-id="1d524-106">此公用程式會要求服務中繼資料文件，以描述資料服務所公開的資料模型。</span><span class="sxs-lookup"><span data-stu-id="1d524-106">The utility requests the service metadata document, which describes the data model exposed by the data service.</span></span> <span data-ttu-id="1d524-107">如需詳細資訊，請參閱[OData：服務元資料檔案](https://go.microsoft.com/fwlink/?LinkId=186070)。</span><span class="sxs-lookup"><span data-stu-id="1d524-107">For more information, see [OData: Service Metadata Document](https://go.microsoft.com/fwlink/?LinkId=186070).</span></span>

- <span data-ttu-id="1d524-108">使用概念結構定義語言（CSDL）定義的資料模型檔案（csdl），如[\[MC-csdl\]：概念結構定義檔案格式](https://go.microsoft.com/fwlink/?LinkID=159072)規格中所定義。</span><span class="sxs-lookup"><span data-stu-id="1d524-108">A data model file (.csdl) defined by using the conceptual schema definition language (CSDL), as defined in the [\[MC-CSDL\]: Conceptual Schema Definition File Format](https://go.microsoft.com/fwlink/?LinkID=159072) specification.</span></span>

- <span data-ttu-id="1d524-109">使用 Entity Framework 提供之實體資料模型所建立的 .edmx 檔案。</span><span class="sxs-lookup"><span data-stu-id="1d524-109">An .edmx file created by using the Entity Data Model tools that are provided with the Entity Framework.</span></span> <span data-ttu-id="1d524-110">如需詳細資訊，請參閱[\[MC-EDMX\]：實體資料模型以取得資料服務封裝格式](https://go.microsoft.com/fwlink/?LinkID=178833)規格。</span><span class="sxs-lookup"><span data-stu-id="1d524-110">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) specification.</span></span>

<span data-ttu-id="1d524-111">如需詳細資訊，請參閱[如何：手動產生用戶端資料服務類別](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1d524-111">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>

<span data-ttu-id="1d524-112">DataSvcUtil 工具會安裝在 .NET Framework 目錄中。</span><span class="sxs-lookup"><span data-stu-id="1d524-112">The DataSvcUtil.exe tool is installed in the .NET Framework directory.</span></span> <span data-ttu-id="1d524-113">在許多情況下，這是位於*c:\windows\microsoft.net\framework\v4.0 加入*中。</span><span class="sxs-lookup"><span data-stu-id="1d524-113">In many cases, this is located in *C:\Windows\Microsoft.NET\Framework\v4.0*.</span></span> <span data-ttu-id="1d524-114">若是64位系統，這會位於*C:\Windows\Microsoft.NET\Framework64\v4.0*中。</span><span class="sxs-lookup"><span data-stu-id="1d524-114">For 64-bit systems, this is located in *C:\Windows\Microsoft.NET\Framework64\v4.0*.</span></span> <span data-ttu-id="1d524-115">您也可以從 Visual Studio 的開發人員命令提示字元存取 DataSvcUtil 工具。</span><span class="sxs-lookup"><span data-stu-id="1d524-115">You can also access the DataSvcUtil.exe tool from Developer Command Prompt for Visual Studio.</span></span>

## <a name="syntax"></a><span data-ttu-id="1d524-116">語法</span><span class="sxs-lookup"><span data-stu-id="1d524-116">Syntax</span></span>

```console
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a><span data-ttu-id="1d524-117">參數</span><span class="sxs-lookup"><span data-stu-id="1d524-117">Parameters</span></span>

|<span data-ttu-id="1d524-118">選項</span><span class="sxs-lookup"><span data-stu-id="1d524-118">Option</span></span>|<span data-ttu-id="1d524-119">描述</span><span class="sxs-lookup"><span data-stu-id="1d524-119">Description</span></span>|
|------------|-----------------|
|`/dataservicecollection`|<span data-ttu-id="1d524-120">指定同時產生將物件繫結至控制項所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1d524-120">Specifies that the code required to bind objects to controls is also generated.</span></span>|
|`/help`<br /><br /> <span data-ttu-id="1d524-121">-或-</span><span class="sxs-lookup"><span data-stu-id="1d524-121">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="1d524-122">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="1d524-122">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="1d524-123">`/in:` *\<檔 >*</span><span class="sxs-lookup"><span data-stu-id="1d524-123">`/in:` *\<file>*</span></span>|<span data-ttu-id="1d524-124">指定 .csdl 或 .edmx 檔案，或是檔案所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="1d524-124">Specifies the .csdl or .edmx file or a directory where the file is located.</span></span>|
|<span data-ttu-id="1d524-125">`/language:`[VB&#124;CSharp]</span><span class="sxs-lookup"><span data-stu-id="1d524-125">`/language:`[VB&#124;CSharp]</span></span>|<span data-ttu-id="1d524-126">指定所產生之原始程式碼檔案的語言。</span><span class="sxs-lookup"><span data-stu-id="1d524-126">Specifies the language for the generated source code files.</span></span> <span data-ttu-id="1d524-127">預設語言為 C#。</span><span class="sxs-lookup"><span data-stu-id="1d524-127">The language defaults to C#.</span></span>|
|`/nologo`|<span data-ttu-id="1d524-128">隱藏著作權訊息。</span><span class="sxs-lookup"><span data-stu-id="1d524-128">Suppresses the copyright message from displaying.</span></span>|
|<span data-ttu-id="1d524-129">`/out:` *\<檔 >*</span><span class="sxs-lookup"><span data-stu-id="1d524-129">`/out:` *\<file>*</span></span>|<span data-ttu-id="1d524-130">指定原始程式碼檔案的名稱，該檔案包含已產生的用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="1d524-130">Specifies the name of the source code file that contains the generated client data service classes.</span></span>|
|<span data-ttu-id="1d524-131">`/uri:` *\<字串 >*</span><span class="sxs-lookup"><span data-stu-id="1d524-131">`/uri:` *\<string>*</span></span>|<span data-ttu-id="1d524-132">OData 摘要的 URI。</span><span class="sxs-lookup"><span data-stu-id="1d524-132">The URI of the OData feed.</span></span>|
|<span data-ttu-id="1d524-133">`/version:`[1.0&#124;2.0]</span><span class="sxs-lookup"><span data-stu-id="1d524-133">`/version:`[1.0&#124;2.0]</span></span>|<span data-ttu-id="1d524-134">指定最高的 OData 已接受版本。</span><span class="sxs-lookup"><span data-stu-id="1d524-134">Specifies the highest accepted version of OData.</span></span> <span data-ttu-id="1d524-135">版本是根據傳回的資料服務中繼資料中 DataService 元素的 `DataServiceVersion` 屬性來決定。</span><span class="sxs-lookup"><span data-stu-id="1d524-135">The version is determined based on the `DataServiceVersion` attribute of the DataService element in the returned data service metadata.</span></span> <span data-ttu-id="1d524-136">如需詳細資訊，請參閱[資料服務版本](data-service-versioning-wcf-data-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="1d524-136">For more information, see [Data Service Versioning](data-service-versioning-wcf-data-services.md).</span></span> <span data-ttu-id="1d524-137">當您指定 `/dataservicecollection` 參數時，您也必須指定 `/version:2.0` 以啟用資料系結。</span><span class="sxs-lookup"><span data-stu-id="1d524-137">When you specify the `/dataservicecollection` parameter, you must also specify `/version:2.0` to enable data binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="1d524-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="1d524-138">See also</span></span>

- [<span data-ttu-id="1d524-139">產生資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="1d524-139">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="1d524-140">如何：新增資料服務參考</span><span class="sxs-lookup"><span data-stu-id="1d524-140">How to: Add a Data Service Reference</span></span>](how-to-add-a-data-service-reference-wcf-data-services.md)
