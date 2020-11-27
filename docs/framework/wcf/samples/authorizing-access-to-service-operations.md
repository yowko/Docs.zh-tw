---
title: 授權存取服務作業
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 68e6d53b656cb6327487598f65fa4f04c2495292
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255451"
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="b420e-102">授權存取服務作業</span><span class="sxs-lookup"><span data-stu-id="b420e-102">Authorizing Access to Service Operations</span></span>

<span data-ttu-id="b420e-103">這個範例會示範如何使用， [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) 以允許使用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 屬性來授權存取服務作業。</span><span class="sxs-lookup"><span data-stu-id="b420e-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="b420e-104">這個範例是以 [消費者入門](getting-started-sample.md) 範例為基礎。</span><span class="sxs-lookup"><span data-stu-id="b420e-104">This sample is based on the [Getting Started](getting-started-sample.md) sample.</span></span> <span data-ttu-id="b420e-105">服務和用戶端是使用來設定的 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="b420e-105">The service and client are configured using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="b420e-106">的 `mode` 屬性已 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 設定為 `Message` ，且已 `clientCredentialType` 設定為 `Windows` 。</span><span class="sxs-lookup"><span data-stu-id="b420e-106">The `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="b420e-107"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 會套用至每個服務方法，並且用來限制每個作業的存取。</span><span class="sxs-lookup"><span data-stu-id="b420e-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="b420e-108">呼叫者必須是 Windows 系統管理員才能存取每個作業。</span><span class="sxs-lookup"><span data-stu-id="b420e-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="b420e-109">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="b420e-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b420e-110">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="b420e-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b420e-111">服務設定檔會使用 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) 來設定 `principalPermissionMode` 屬性：</span><span class="sxs-lookup"><span data-stu-id="b420e-111">The service configuration file uses the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="b420e-112">將 `principalPermissionMode` 設定為 `UseWindowsGroups`，便可以根據 Windows 群組名稱來使用 <xref:System.Security.Permissions.PrincipalPermissionAttribute>。</span><span class="sxs-lookup"><span data-stu-id="b420e-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="b420e-113"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 會套用至每個作業以要求呼叫者必須是 Windows Administrators 群組的成員，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="b420e-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="b420e-114">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="b420e-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b420e-115">如果用戶端是以 Administrators 群組成員的帳戶執行，該用戶端便能與每個作業進行成功通訊，否則就會拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="b420e-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="b420e-116">為了體驗授權失敗，這時要使用不屬於 Administrators 群組的帳戶來執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="b420e-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="b420e-117">在主控台視窗中按 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="b420e-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="b420e-118">藉由實作 <xref:System.ServiceModel.Dispatcher.IErrorHandler>，即可向服務通知授權失敗。</span><span class="sxs-lookup"><span data-stu-id="b420e-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="b420e-119">如需有關實施的詳細資訊，請參閱 [擴充對錯誤處理和報告的控制](extending-control-over-error-handling-and-reporting.md) `IErrorHandler` 。</span><span class="sxs-lookup"><span data-stu-id="b420e-119">See [Extending Control Over Error Handling and Reporting](extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b420e-120">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="b420e-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b420e-121">確定您已 [針對 Windows Communication Foundation 範例執行一次性安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b420e-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b420e-122">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="b420e-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b420e-123">若要在單一或跨電腦的設定中執行範例，請遵循執行 [Windows Communication Foundation 範例](running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="b420e-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
