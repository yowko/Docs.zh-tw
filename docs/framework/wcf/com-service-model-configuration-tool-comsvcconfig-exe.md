---
title: COM+ 服務模型組態工具 (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 6d0967355e64640e0fd5c81f04a5bf4f33c7b3f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158654"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="78bc4-102">COM+ 服務模型組態工具 (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="78bc4-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="78bc4-103">COM+ 服務模型組態命令列工具 (ComSvcConfig.exe) 可讓您設定要公開為 Web 服務的 COM+ 介面。</span><span class="sxs-lookup"><span data-stu-id="78bc4-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78bc4-104">語法</span><span class="sxs-lookup"><span data-stu-id="78bc4-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="78bc4-105">備註</span><span class="sxs-lookup"><span data-stu-id="78bc4-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78bc4-106">您必須是本機電腦的系統管理員，才能使用 ComSvcConfig.exe。</span><span class="sxs-lookup"><span data-stu-id="78bc4-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="78bc4-107">您可以在下列位置找到這個工具</span><span class="sxs-lookup"><span data-stu-id="78bc4-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="78bc4-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span><span class="sxs-lookup"><span data-stu-id="78bc4-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
 <span data-ttu-id="78bc4-109">如需 ComSvcConfig.exe 的詳細資訊，請參閱[How to:使用 COM + 服務模型組態工具](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="78bc4-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="78bc4-110">下表說明可以和 ComSvcConfig.exe 搭配使用的模式。</span><span class="sxs-lookup"><span data-stu-id="78bc4-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="78bc4-111">選項</span><span class="sxs-lookup"><span data-stu-id="78bc4-111">Option</span></span>|<span data-ttu-id="78bc4-112">描述</span><span class="sxs-lookup"><span data-stu-id="78bc4-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="78bc4-113">安裝服務模型整合的 COM+ 介面組態。</span><span class="sxs-lookup"><span data-stu-id="78bc4-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="78bc4-114">簡短形式：`/i`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="78bc4-115">解除安裝服務模型整合的 COM+ 介面組態。</span><span class="sxs-lookup"><span data-stu-id="78bc4-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="78bc4-116">簡短形式：`/u`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="78bc4-117">列出 COM+ 應用程式和元件的相關資訊，這些應用程式和元件具有針對服務模型整合設定的介面。</span><span class="sxs-lookup"><span data-stu-id="78bc4-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="78bc4-118">簡短形式：`/l`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="78bc4-119">下表說明可以和 ComSvcConfig.exe 搭配使用的旗標。</span><span class="sxs-lookup"><span data-stu-id="78bc4-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="78bc4-120">選項</span><span class="sxs-lookup"><span data-stu-id="78bc4-120">Option</span></span>|<span data-ttu-id="78bc4-121">描述</span><span class="sxs-lookup"><span data-stu-id="78bc4-121">Description</span></span>|  
|------------|-----------------|  
|`/application:` <span data-ttu-id="78bc4-122">\<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="78bc4-122">\<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="78bc4-123">指定要設定的 COM+ 應用程式。</span><span class="sxs-lookup"><span data-stu-id="78bc4-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="78bc4-124">簡短形式：`/a`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-124">Short form `/a`.</span></span>|  
|`/contract:` <span data-ttu-id="78bc4-125">\<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="78bc4-125">\<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="78bc4-126">指定要設定為服務合約的 COM+ 元件和介面。</span><span class="sxs-lookup"><span data-stu-id="78bc4-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="78bc4-127">簡短形式：`/c`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="78bc4-128">雖然萬用字元 (\*) 可在您指定的元件和介面的名稱，我們建議您不要使用它，因為您可能會公開您不想要的介面。</span><span class="sxs-lookup"><span data-stu-id="78bc4-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|`/hosting:` <span data-ttu-id="78bc4-129">\<*complus*  &#124; *was*\></span><span class="sxs-lookup"><span data-stu-id="78bc4-129">\<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="78bc4-130">指定使用 COM+ 主控模式或 Web 主控模式。</span><span class="sxs-lookup"><span data-stu-id="78bc4-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="78bc4-131">簡短形式：`/h`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="78bc4-132">使用 COM+ 主控模式必須明確啟動 COM+ 應用程式。</span><span class="sxs-lookup"><span data-stu-id="78bc4-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="78bc4-133">使用 Web 主控模式可讓 COM+ 應用程式視需要自動啟動。</span><span class="sxs-lookup"><span data-stu-id="78bc4-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="78bc4-134">如果 COM+ 應用程式是程式庫應用程式，它會在網際網路資訊服務 (IIS) 處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="78bc4-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="78bc4-135">如果 COM+ 應用程式是伺服器應用程式，它會在 Dllhost.exe 處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="78bc4-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|`/webSite:` <span data-ttu-id="78bc4-136">\<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="78bc4-136">\<*WebsiteName*\></span></span>|<span data-ttu-id="78bc4-137">指定使用 Web 主控模式時用於主控的網站 (請參閱 `/hosting` 旗標)。</span><span class="sxs-lookup"><span data-stu-id="78bc4-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="78bc4-138">簡短形式：`/w`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="78bc4-139">如果未指定網站，則會使用預設網站。</span><span class="sxs-lookup"><span data-stu-id="78bc4-139">If no Web site is specified, the default Web site is used.</span></span>|  
|`/webDirectory:` <span data-ttu-id="78bc4-140">\<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="78bc4-140">\<*WebDirectoryName*\></span></span>|<span data-ttu-id="78bc4-141">指定使用 Web 主控模式時用於主控的虛擬目錄 (請參閱 `/hosting` 旗標)。</span><span class="sxs-lookup"><span data-stu-id="78bc4-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="78bc4-142">簡短形式：`/d`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="78bc4-143">將 Metadata Exchange (MEX) 服務端點新增至預設服務組態，以支援要從服務擷取合約定義的用戶端。</span><span class="sxs-lookup"><span data-stu-id="78bc4-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="78bc4-144">簡短形式：`/x`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="78bc4-145">以 ID 的方式顯示應用程式、元件和介面資訊。</span><span class="sxs-lookup"><span data-stu-id="78bc4-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="78bc4-146">簡短形式：`/k`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="78bc4-147">防止 ComSvcConfig.exe 顯示其標誌。</span><span class="sxs-lookup"><span data-stu-id="78bc4-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="78bc4-148">簡短形式：`/n`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="78bc4-149">除了發生的任何錯誤之外，也輸出所有的警告或資訊文字。</span><span class="sxs-lookup"><span data-stu-id="78bc4-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="78bc4-150">簡短形式：`/v`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="78bc4-151">顯示使用方式訊息。</span><span class="sxs-lookup"><span data-stu-id="78bc4-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="78bc4-152">簡短形式：`/?`。</span><span class="sxs-lookup"><span data-stu-id="78bc4-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="78bc4-153">當指定的介面包含一或多個可公開的方法簽章時，產生服務組態。</span><span class="sxs-lookup"><span data-stu-id="78bc4-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="78bc4-154">在服務初始化階段，相容的方法會顯示為服務合約上的作業，不相容的方法會被忽略，且不會出現在服務合約中。</span><span class="sxs-lookup"><span data-stu-id="78bc4-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="78bc4-155">如果缺少這個旗標，當指定的介面包含一或多個不相容的方法時，工具不會產生服務組態。</span><span class="sxs-lookup"><span data-stu-id="78bc4-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="78bc4-156">範例</span><span class="sxs-lookup"><span data-stu-id="78bc4-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="78bc4-157">描述</span><span class="sxs-lookup"><span data-stu-id="78bc4-157">Description</span></span>  
 <span data-ttu-id="78bc4-158">下列範例說明使用 COM+ 主控模式，將 `IFinances` 元件的 (取自 OnlineStore COM+ 應用程式) `ItemOrders.IFinancial` 介面新增至公開為 Web 服務的介面組。</span><span class="sxs-lookup"><span data-stu-id="78bc4-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="78bc4-159">除了發生的任何錯誤之外，也輸出所有的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="78bc4-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="78bc4-160">程式碼</span><span class="sxs-lookup"><span data-stu-id="78bc4-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="78bc4-161">描述</span><span class="sxs-lookup"><span data-stu-id="78bc4-161">Description</span></span>  
 <span data-ttu-id="78bc4-162">下列範例說明使用 Web 主控模式，將 `IStockLevels` 元件的 (取自 OnlineWarehouse COM+ 應用程式) `ItemInventory.Warehouse` 介面新增至公開為 Web 服務的介面組。</span><span class="sxs-lookup"><span data-stu-id="78bc4-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="78bc4-163">Web 服務是由 IIS 的 OnlineWarehouse 虛擬目錄進行 Web 主控。</span><span class="sxs-lookup"><span data-stu-id="78bc4-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="78bc4-164">程式碼</span><span class="sxs-lookup"><span data-stu-id="78bc4-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="78bc4-165">描述</span><span class="sxs-lookup"><span data-stu-id="78bc4-165">Description</span></span>  
 <span data-ttu-id="78bc4-166">下列範例說明從公開為 Web 服務的介面組中移除 `IFinances` 元件的 (取自 OnlineStore COM+ 應用程式) `ItemOrders.Financial` 介面。</span><span class="sxs-lookup"><span data-stu-id="78bc4-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="78bc4-167">程式碼</span><span class="sxs-lookup"><span data-stu-id="78bc4-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="78bc4-168">描述</span><span class="sxs-lookup"><span data-stu-id="78bc4-168">Description</span></span>  
 <span data-ttu-id="78bc4-169">下列範例列出本機電腦上 OnlineStore COM+ 應用程式目前公開的 COM+ 主控介面，以及對應的位址與繫結詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="78bc4-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="78bc4-170">程式碼</span><span class="sxs-lookup"><span data-stu-id="78bc4-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="78bc4-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78bc4-171">See also</span></span>

- [<span data-ttu-id="78bc4-172">HOW TO：使用 COM+ 服務模型組態工具</span><span class="sxs-lookup"><span data-stu-id="78bc4-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
