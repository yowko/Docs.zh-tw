---
title: 同處理序並存執行
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89dfe697f49e8144d15586cc9c1075f69d1f3a07
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816048"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="0ae96-102">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="0ae96-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="0ae96-103">從 .NET Framework 4 開始，您可以使用同處理序並存裝載，在單一處理序中執行多個 Common Language Runtime (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="0ae96-103">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="0ae96-104">根據預設，Managed COM 元件會與建置它們的 .NET Framework 版本一起執行，不論針對程序所載入的 .NET Framework 版本為何。</span><span class="sxs-lookup"><span data-stu-id="0ae96-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="0ae96-105">背景</span><span class="sxs-lookup"><span data-stu-id="0ae96-105">Background</span></span>  
 <span data-ttu-id="0ae96-106">.NET Framework 一律會提供受控碼應用程式的並存裝載，但在 .NET Framework 4 之前，並未針對受控 COM 元件提供該功能。</span><span class="sxs-lookup"><span data-stu-id="0ae96-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="0ae96-107">過去，載入至程序的 Managed COM 元件是與已載入的執行階段版本或 .NET Framework 的最新已安裝版本一起執行。</span><span class="sxs-lookup"><span data-stu-id="0ae96-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="0ae96-108">如果此版本與 COM 元件不相容，元件就會失敗。</span><span class="sxs-lookup"><span data-stu-id="0ae96-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="0ae96-109">.NET Framework 4 提供新的方式進行並存裝載，以確保下列各項：</span><span class="sxs-lookup"><span data-stu-id="0ae96-109">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="0ae96-110">安裝新版的 .NET Framework 不會影響現有應用程式。</span><span class="sxs-lookup"><span data-stu-id="0ae96-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="0ae96-111">應用程式會針對用來建置的 .NET Framework 版本執行。</span><span class="sxs-lookup"><span data-stu-id="0ae96-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="0ae96-112">除非明確指示，否則它們不會使用新版 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="0ae96-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="0ae96-113">不過，應用程式較容易轉換成使用新版 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="0ae96-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="0ae96-114">使用者和開發人員的影響</span><span class="sxs-lookup"><span data-stu-id="0ae96-114">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="0ae96-115">**一般使用者和系統管理員**.</span><span class="sxs-lookup"><span data-stu-id="0ae96-115">**End users and system administrators**.</span></span> <span data-ttu-id="0ae96-116">這些使用者現在可以更有信心，在單獨或與應用程式一起安裝新版執行階段時，不會對其電腦造成任何影響。</span><span class="sxs-lookup"><span data-stu-id="0ae96-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="0ae96-117">現有應用程式會繼續與之前一樣地執行。</span><span class="sxs-lookup"><span data-stu-id="0ae96-117">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="0ae96-118">**應用程式開發人員**。</span><span class="sxs-lookup"><span data-stu-id="0ae96-118">**Application developers**.</span></span> <span data-ttu-id="0ae96-119">並存裝載幾乎不會影響應用程式開發人員。</span><span class="sxs-lookup"><span data-stu-id="0ae96-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="0ae96-120">根據預設，應用程式一律會針對用來建置的 .NET Framework 版本執行；這並未變更。</span><span class="sxs-lookup"><span data-stu-id="0ae96-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="0ae96-121">不過，開發人員可以覆寫這個行為，並指示應用程式在較新版的 .NET Framework 下執行 (請參閱[情節 2](#scenarios))。</span><span class="sxs-lookup"><span data-stu-id="0ae96-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="0ae96-122">**程式庫開發人員和取用者**。</span><span class="sxs-lookup"><span data-stu-id="0ae96-122">**Library developers and consumers**.</span></span> <span data-ttu-id="0ae96-123">並存裝載無法解決程式庫開發人員所面對的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="0ae96-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="0ae96-124">應用程式直接透過直接參考或 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 呼叫所載入的程式庫，會持續使用載入它之 <xref:System.AppDomain> 的執行階段。</span><span class="sxs-lookup"><span data-stu-id="0ae96-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="0ae96-125">您應該針對您想要支援的所有 .NET Framework 版本測試程式庫。</span><span class="sxs-lookup"><span data-stu-id="0ae96-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="0ae96-126">如果使用 .NET Framework 4 執行階段來編譯應用程式，但應用程式包括使用舊版執行階段所建置的程式庫，則該程式庫也會使用 .NET Framework 4 執行階段。</span><span class="sxs-lookup"><span data-stu-id="0ae96-126">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="0ae96-127">不過，如果您的應用程式是使用舊版執行階段所建置，且程式庫是使用 .NET Framework 4 所建置，則您必須強制應用程式使用 .NET Framework 4 (請參閱[情節 3](#scenarios))。</span><span class="sxs-lookup"><span data-stu-id="0ae96-127">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="0ae96-128">**Managed COM 元件開發人員**。</span><span class="sxs-lookup"><span data-stu-id="0ae96-128">**Managed COM component developers**.</span></span> <span data-ttu-id="0ae96-129">過去，會使用電腦上所安裝的最新執行階段版本來自動執行 Managed COM 元件。</span><span class="sxs-lookup"><span data-stu-id="0ae96-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="0ae96-130">您現在可以針對建置它們的執行階段版本執行 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="0ae96-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="0ae96-131">如下表所示，使用 .NET Framework 1.1 版所建置的元件可以與第 4 版元件並存執行，但它們無法與 2.0、3.0 或 3.5 版元件一起執行，因為這些版本無法使用並存裝載。</span><span class="sxs-lookup"><span data-stu-id="0ae96-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="0ae96-132">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="0ae96-132">.NET Framework version</span></span>|<span data-ttu-id="0ae96-133">1.1</span><span class="sxs-lookup"><span data-stu-id="0ae96-133">1.1</span></span>|<span data-ttu-id="0ae96-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="0ae96-134">2.0 - 3.5</span></span>|<span data-ttu-id="0ae96-135">4</span><span class="sxs-lookup"><span data-stu-id="0ae96-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="0ae96-136">1.1</span><span class="sxs-lookup"><span data-stu-id="0ae96-136">1.1</span></span>|<span data-ttu-id="0ae96-137">不適用</span><span class="sxs-lookup"><span data-stu-id="0ae96-137">Not applicable</span></span>|<span data-ttu-id="0ae96-138">否</span><span class="sxs-lookup"><span data-stu-id="0ae96-138">No</span></span>|<span data-ttu-id="0ae96-139">[是]</span><span class="sxs-lookup"><span data-stu-id="0ae96-139">Yes</span></span>|  
    |<span data-ttu-id="0ae96-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="0ae96-140">2.0 - 3.5</span></span>|<span data-ttu-id="0ae96-141">否</span><span class="sxs-lookup"><span data-stu-id="0ae96-141">No</span></span>|<span data-ttu-id="0ae96-142">不適用</span><span class="sxs-lookup"><span data-stu-id="0ae96-142">Not applicable</span></span>|<span data-ttu-id="0ae96-143">是</span><span class="sxs-lookup"><span data-stu-id="0ae96-143">Yes</span></span>|  
    |<span data-ttu-id="0ae96-144">4</span><span class="sxs-lookup"><span data-stu-id="0ae96-144">4</span></span>|<span data-ttu-id="0ae96-145">[是]</span><span class="sxs-lookup"><span data-stu-id="0ae96-145">Yes</span></span>|<span data-ttu-id="0ae96-146">是</span><span class="sxs-lookup"><span data-stu-id="0ae96-146">Yes</span></span>|<span data-ttu-id="0ae96-147">不適用</span><span class="sxs-lookup"><span data-stu-id="0ae96-147">Not applicable</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="0ae96-148">.NET Framework 3.0 和 3.5 版是根據 2.0 版透過累加方式所建置，不需要並存執行。</span><span class="sxs-lookup"><span data-stu-id="0ae96-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="0ae96-149">這些本質上是相同的版本。</span><span class="sxs-lookup"><span data-stu-id="0ae96-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="0ae96-150">常見並存裝載案例</span><span class="sxs-lookup"><span data-stu-id="0ae96-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="0ae96-151">**情節 1：** 使用舊版 .NET Framework 所建置 COM 元件的原生應用程式。</span><span class="sxs-lookup"><span data-stu-id="0ae96-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="0ae96-152">已安裝的 .NET Framework 版本：COM 元件使用的 .NET Framework 4 以及所有其他 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="0ae96-152">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="0ae96-153">處理方式：在此情節中，不執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="0ae96-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="0ae96-154">COM 元件會與註冊它們的 .NET Framework 版本一起執行。</span><span class="sxs-lookup"><span data-stu-id="0ae96-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="0ae96-155">**情節 2**：您想同時執行使用 .NET Framework 2.0 SP1 建置的受控應用程式與 [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)]，但也願意在 .NET Framework 2.0 版不存在時，於 .NET Framework 4 上執行。</span><span class="sxs-lookup"><span data-stu-id="0ae96-155">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="0ae96-156">已安裝的 .NET Framework 版本：舊版 .NET Framework 和 .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="0ae96-156">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="0ae96-157">處理方式：在應用程式目錄的[應用程式組態檔](../../../docs/framework/configure-apps/index.md)中，使用 [\<startup> 項目](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)和 [\<supportedRuntime> 項目](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)，其設定方式如下：</span><span class="sxs-lookup"><span data-stu-id="0ae96-157">What to do: In the [application configuration file](../../../docs/framework/configure-apps/index.md) in the application directory, use the [\<startup> element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="0ae96-158">**情節 3：** 原生應用程式使用舊版 .NET Framework 所建置的 COM 元件，而您想要將其與 .NET Framework 4 一起執行。</span><span class="sxs-lookup"><span data-stu-id="0ae96-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="0ae96-159">已安裝的 .NET Framework 版本：.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="0ae96-159">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="0ae96-160">處理方式：在應用程式目錄的應用程式組態檔中，搭配使用 `<startup>` 項目與設為 `true` 的 `useLegacyV2RuntimeActivationPolicy` 屬性以及設定如下的 `<supportedRuntime>` 項目：</span><span class="sxs-lookup"><span data-stu-id="0ae96-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="0ae96-161">範例</span><span class="sxs-lookup"><span data-stu-id="0ae96-161">Example</span></span>  
 <span data-ttu-id="0ae96-162">下列範例示範執行 Managed COM 元件的 Unmanaged COM 主機，方法是使用編譯元件使用的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="0ae96-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="0ae96-163">若要執行下列範例，請編譯並註冊下列使用 .NET Framework 3.5 的受控 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="0ae96-163">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="0ae96-164">若要註冊元件，請在 [專案]  功能表上按一下 [屬性]  ，再按一下 [組建]  索引標籤，然後選取 [註冊 COM Interop]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0ae96-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Runtime.InteropServices;  
  
namespace BasicComObject  
{  
    [ComVisible(true), Guid("9C99C4B5-CA54-4c58-8988-49B6811BA53B")]  
    public class MyObject : SimpleObjectModel.IPrintInfo  
    {  
        public MyObject()  
        {  
        }  
        public void PrintInfo()  
        {  
            Console.WriteLine("MyObject was activated in {0} runtime in:\n\tAppDomain {1}:{2}", System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion(), AppDomain.CurrentDomain.Id, AppDomain.CurrentDomain.FriendlyName);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="0ae96-165">編譯下列 Unmanaged C++ 應用程式，以啟用前一個範例所建立的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="0ae96-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
```cpp
#include "stdafx.h"  
#include <string>  
#include <iostream>  
#include <objbase.h>  
#include <string.h>  
#include <process.h>  
  
using namespace std;  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    char input;  
    CoInitialize(NULL) ;  
    CLSID clsid;  
    HRESULT hr;  
    HRESULT clsidhr = CLSIDFromString(L"{9C99C4B5-CA54-4c58-8988-49B6811BA53B}",&clsid);  
    hr = -1;  
    if (FAILED(clsidhr))  
    {  
        printf("Failed to construct CLSID from String\n");  
    }  
    UUID id = __uuidof(IUnknown);  
    IUnknown * pUnk = NULL;  
    hr = ::CoCreateInstance(clsid,NULL,CLSCTX_INPROC_SERVER,id,(void **) &pUnk);  
    if (FAILED(hr))  
    {  
        printf("Failed CoCreateInstance\n");  
    }else  
    {  
        pUnk->AddRef();  
        printf("Succeeded\n");  
    }  
  
    DISPID dispid;  
    IDispatch* pPrintInfo;  
    pUnk->QueryInterface(IID_IDispatch, (void**)&pPrintInfo);  
    OLECHAR FAR* szMethod[1];  
    szMethod[0]=OLESTR("PrintInfo");   
    hr = pPrintInfo->GetIDsOfNames(IID_NULL,szMethod, 1, LOCALE_SYSTEM_DEFAULT, &dispid);  
    DISPPARAMS dispparams;  
    dispparams.cNamedArgs = 0;  
    dispparams.cArgs = 0;  
    VARIANTARG* pvarg = NULL;  
    EXCEPINFO * pexcepinfo = NULL;  
    WORD wFlags = DISPATCH_METHOD ;  
;  
    LPVARIANT pvRet = NULL;  
    UINT * pnArgErr = NULL;  
    hr = pPrintInfo->Invoke(dispid,IID_NULL, LOCALE_USER_DEFAULT, wFlags,  
        &dispparams, pvRet, pexcepinfo, pnArgErr);  
    printf("Press Enter to exit");  
    scanf_s("%c",&input);  
    CoUninitialize();  
    return 0;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ae96-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ae96-166">See also</span></span>

- [<span data-ttu-id="0ae96-167">\<startup> 項目</span><span class="sxs-lookup"><span data-stu-id="0ae96-167">\<startup> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="0ae96-168">\<supportedRuntime> 項目</span><span class="sxs-lookup"><span data-stu-id="0ae96-168">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
