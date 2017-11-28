---
title: "WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06c7107fe58647d29146ed5ef4cc31fc9004d2b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a><span data-ttu-id="1653e-102">WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="1653e-102">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>
<span data-ttu-id="1653e-103">DataSvcUtil.exe 是所提供的命令列工具[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]會取用[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]摘要，並產生從.NET Framework 用戶端應用程式存取資料服務所需的用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="1653e-103">DataSvcUtil.exe is a command-line tool provided by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] that consumes an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed and generates the client data service classes that are needed to access a data service from a .NET Framework client application.</span></span> <span data-ttu-id="1653e-104">此公用程式可以透過使用下列中繼資料來源產生資料類別：</span><span class="sxs-lookup"><span data-stu-id="1653e-104">This utility can generate data classes by using the following metadata sources:</span></span>  
  
-   <span data-ttu-id="1653e-105">資料服務的根 URI。</span><span class="sxs-lookup"><span data-stu-id="1653e-105">The root URI of a data service.</span></span> <span data-ttu-id="1653e-106">此公用程式會要求服務中繼資料文件，以描述資料服務所公開的資料模型。</span><span class="sxs-lookup"><span data-stu-id="1653e-106">The utility requests the service metadata document, which describes the data model exposed by the data service.</span></span> <span data-ttu-id="1653e-107">如需詳細資訊，請參閱[OData： 服務中繼資料文件](http://go.microsoft.com/fwlink/?LinkId=186070)。</span><span class="sxs-lookup"><span data-stu-id="1653e-107">For more information, see [OData: Service Metadata Document](http://go.microsoft.com/fwlink/?LinkId=186070).</span></span>  
  
-   <span data-ttu-id="1653e-108">定義使用概念結構定義語言 (CSDL)，如中所定義的資料模型檔案 (.csdl) [ \[MC-CSDL\]： 概念結構定義檔案格式](http://go.microsoft.com/fwlink/?LinkID=159072)規格。</span><span class="sxs-lookup"><span data-stu-id="1653e-108">A data model file (.csdl) defined by using the conceptual schema definition language (CSDL), as defined in the [\[MC-CSDL\]: Conceptual Schema Definition File Format](http://go.microsoft.com/fwlink/?LinkID=159072) specification.</span></span>  
  
-   <span data-ttu-id="1653e-109">使用 Entity Framework 提供之實體資料模型所建立的 .edmx 檔案。</span><span class="sxs-lookup"><span data-stu-id="1653e-109">An .edmx file created by using the Entity Data Model tools that are provided with the Entity Framework.</span></span> <span data-ttu-id="1653e-110">如需詳細資訊，請參閱[ \[MC-EDMX\]： 資料服務封裝格式的實體資料模型](http://go.microsoft.com/fwlink/?LinkID=178833)規格。</span><span class="sxs-lookup"><span data-stu-id="1653e-110">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](http://go.microsoft.com/fwlink/?LinkID=178833) specification.</span></span>  
  
 <span data-ttu-id="1653e-111">如需詳細資訊，請參閱[How to： 手動產生用戶端資料服務類別](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1653e-111">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="1653e-112">DataSvcUtil.exe 工具安裝在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 目錄中。</span><span class="sxs-lookup"><span data-stu-id="1653e-112">The DataSvcUtil.exe tool is installed in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory.</span></span> <span data-ttu-id="1653e-113">在許多情況下，這會位於 C:\Windows\Microsoft.NET\Framework\v4.0。</span><span class="sxs-lookup"><span data-stu-id="1653e-113">In many cases, this is located in C:\Windows\Microsoft.NET\Framework\v4.0,.</span></span> <span data-ttu-id="1653e-114">若為 64 位元系統，則是位於 C:\Windows\Microsoft.NET\Framework64\v4.0。</span><span class="sxs-lookup"><span data-stu-id="1653e-114">For 64-bit systems, this is located in C:\Windows\Microsoft.NET\Framework64\v4.0.</span></span> <span data-ttu-id="1653e-115">您也可以從 Visual Studio 命令提示字元存取 DataSvcUtil.exe 工具 (按一下**啟動**，指向 **所有程式**，指向  **Microsoft Visual Studio 2010**，指向**Visual Studio Tools**，然後按一下  **Visual Studio 2010 命令提示字元**)。</span><span class="sxs-lookup"><span data-stu-id="1653e-115">You can also access the DataSvcUtil.exe tool from the Visual Studio command prompt (Click **Start**, point to **All Programs**, point to **Microsoft Visual Studio 2010**, point to **Visual Studio Tools**, and then click **Visual Studio 2010 Command Prompt**).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1653e-116">語法</span><span class="sxs-lookup"><span data-stu-id="1653e-116">Syntax</span></span>  
  
```  
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1653e-117">參數</span><span class="sxs-lookup"><span data-stu-id="1653e-117">Parameters</span></span>  
  
|<span data-ttu-id="1653e-118">選項</span><span class="sxs-lookup"><span data-stu-id="1653e-118">Option</span></span>|<span data-ttu-id="1653e-119">描述</span><span class="sxs-lookup"><span data-stu-id="1653e-119">Description</span></span>|  
|------------|-----------------|  
|`/dataservicecollection`|<span data-ttu-id="1653e-120">指定同時產生將物件繫結至控制項所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1653e-120">Specifies that the code required to bind objects to controls is also generated.</span></span>|  
|`/help`<br /><br /> <span data-ttu-id="1653e-121">-或-</span><span class="sxs-lookup"><span data-stu-id="1653e-121">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="1653e-122">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="1653e-122">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="1653e-123">`/in:`*\<檔案 >*</span><span class="sxs-lookup"><span data-stu-id="1653e-123">`/in:` *\<file>*</span></span>|<span data-ttu-id="1653e-124">指定 .csdl 或 .edmx 檔案，或是檔案所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="1653e-124">Specifies the .csdl or .edmx file or a directory where the file is located.</span></span>|  
|<span data-ttu-id="1653e-125">`/language:`[VB &#124;CSharp]</span><span class="sxs-lookup"><span data-stu-id="1653e-125">`/language:`[VB&#124;CSharp]</span></span>|<span data-ttu-id="1653e-126">指定所產生之原始程式碼檔案的語言。</span><span class="sxs-lookup"><span data-stu-id="1653e-126">Specifies the language for the generated source code files.</span></span> <span data-ttu-id="1653e-127">預設語言為 C#。</span><span class="sxs-lookup"><span data-stu-id="1653e-127">The language defaults to C#.</span></span>|  
|`/nologo`|<span data-ttu-id="1653e-128">隱藏著作權訊息。</span><span class="sxs-lookup"><span data-stu-id="1653e-128">Suppresses the copyright message from displaying.</span></span>|  
|<span data-ttu-id="1653e-129">`/out:`*\<檔案 >*</span><span class="sxs-lookup"><span data-stu-id="1653e-129">`/out:` *\<file>*</span></span>|<span data-ttu-id="1653e-130">指定原始程式碼檔案的名稱，該檔案包含已產生的用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="1653e-130">Specifies the name of the source code file that contains the generated client data service classes.</span></span>|  
|<span data-ttu-id="1653e-131">`/uri:`*\<字串 >*</span><span class="sxs-lookup"><span data-stu-id="1653e-131">`/uri:` *\<string>*</span></span>|<span data-ttu-id="1653e-132">URI[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要。</span><span class="sxs-lookup"><span data-stu-id="1653e-132">The URI of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span>|  
|<span data-ttu-id="1653e-133">`/version:`[1.0&#124;2.0]</span><span class="sxs-lookup"><span data-stu-id="1653e-133">`/version:`[1.0&#124;2.0]</span></span>|<span data-ttu-id="1653e-134">指定 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 的最高接受版本。</span><span class="sxs-lookup"><span data-stu-id="1653e-134">Specifies the highest accepted version of [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> <span data-ttu-id="1653e-135">決定版本是根據`DataServiceVersion`DataService 中項目的屬性傳回的資料服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1653e-135">The version is determined based on the `DataServiceVersion` attribute of the DataService element in the returned data service metadata.</span></span> <span data-ttu-id="1653e-136">如需詳細資訊，請參閱[資料服務版本控制](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1653e-136">For more information, see [Data Service Versioning](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).</span></span> <span data-ttu-id="1653e-137">當您指定`/dataservicecollection`參數，您也必須指定`/version:2.0`以啟用資料繫結。</span><span class="sxs-lookup"><span data-stu-id="1653e-137">When you specify the `/dataservicecollection` parameter, you must also specify `/version:2.0` to enable data binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1653e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1653e-138">See Also</span></span>  
 [<span data-ttu-id="1653e-139">產生資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="1653e-139">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [<span data-ttu-id="1653e-140">如何： 加入資料服務參考</span><span class="sxs-lookup"><span data-stu-id="1653e-140">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
