---
title: HOW TO：使用 Svcutil.exe 來驗證已編譯服務程式碼
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 599f5624b7eb0c32cbcc0a78e6c7f989ce470b58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312419"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="575d1-102">HOW TO：使用 Svcutil.exe 來驗證已編譯服務程式碼</span><span class="sxs-lookup"><span data-stu-id="575d1-102">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>
<span data-ttu-id="575d1-103">您可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來偵測服務實作和組態中的錯誤，而不需要裝載服務。</span><span class="sxs-lookup"><span data-stu-id="575d1-103">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="575d1-104">若要驗證服務</span><span class="sxs-lookup"><span data-stu-id="575d1-104">To validate a service</span></span>  
  
1. <span data-ttu-id="575d1-105">將服務編譯為可執行檔以及一或多個相依組件。</span><span class="sxs-lookup"><span data-stu-id="575d1-105">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2. <span data-ttu-id="575d1-106">開啟 SDK 命令提示字元</span><span class="sxs-lookup"><span data-stu-id="575d1-106">Open an SDK command prompt</span></span>  
  
3. <span data-ttu-id="575d1-107">在命令提示字元中，使用下列格式啟動 Svcutil.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="575d1-107">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="575d1-108">如需有關的各種參數的詳細資訊，請參閱的服務 Validationsection [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)主題。</span><span class="sxs-lookup"><span data-stu-id="575d1-108">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="575d1-109">您必須使用 `/serviceName` 選項以指出您要驗證的服務組態名稱。</span><span class="sxs-lookup"><span data-stu-id="575d1-109">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="575d1-110">`assemblyPath` 引數會指定服務的可執行檔和一或多個組件的路徑，而這些組件中含有要驗證的服務類型。</span><span class="sxs-lookup"><span data-stu-id="575d1-110">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="575d1-111">可執行組件必須具有相關聯的組態檔，才能提供服務組態。</span><span class="sxs-lookup"><span data-stu-id="575d1-111">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="575d1-112">您可以使用標準命令列萬用字元來提供多個組件。</span><span class="sxs-lookup"><span data-stu-id="575d1-112">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="575d1-113">範例</span><span class="sxs-lookup"><span data-stu-id="575d1-113">Example</span></span>  
 <span data-ttu-id="575d1-114">下列命令會執行在 myServiceHost.exe 可執行檔中實作的服務 myServiceName。</span><span class="sxs-lookup"><span data-stu-id="575d1-114">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="575d1-115">將會自動載入服務的組態檔 (myServiceHost.exe.config)。</span><span class="sxs-lookup"><span data-stu-id="575d1-115">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="575d1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="575d1-116">See also</span></span>

- [<span data-ttu-id="575d1-117">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="575d1-117">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
