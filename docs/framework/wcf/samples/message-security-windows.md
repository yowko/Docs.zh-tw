---
title: "訊息安全性視窗"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
caps.latest.revision: "34"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c8bb8d0506dd535a312bd8df8954c8143d9543ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-windows"></a><span data-ttu-id="0f63d-102">訊息安全性視窗</span><span class="sxs-lookup"><span data-stu-id="0f63d-102">Message Security Windows</span></span>
<span data-ttu-id="0f63d-103">這個範例會示範如何將 <xref:System.ServiceModel.WSHttpBinding> 繫結設定成搭配 Windows 驗證使用的訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="0f63d-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="0f63d-104">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0f63d-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="0f63d-105">在這個範例中，服務會由網際網路資訊服務 (IIS) 裝載，而用戶端是主控台應用程式 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="0f63d-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f63d-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="0f63d-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0f63d-107">預設安全性[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)是使用 Windows 驗證的訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="0f63d-107">The default security for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="0f63d-108">在此範例中的組態檔明確設定`mode`屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)至`Message`和`clientCredentialType`屬性`Windows`。</span><span class="sxs-lookup"><span data-stu-id="0f63d-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="0f63d-109">這些值是這個繫結的預設值，但是已經明確設定成可示範其使用方式，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="0f63d-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="0f63d-110">用戶端端點組態是由服務端點的絕對位址、繫結及合約所組成。</span><span class="sxs-lookup"><span data-stu-id="0f63d-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="0f63d-111">用戶端繫結是透過適當的 `securityMode` 和 `authenticationMode` 所設定。</span><span class="sxs-lookup"><span data-stu-id="0f63d-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"   
            binding="wsHttpBinding"   
            bindingConfiguration="Binding1"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      <!--The default security for the WSHttpBinding is-->  
      <!--Message security using Windows authentication. -->  
      <!--This configuration explicitly defines the security mode -->  
      <!--as Message and the clientCredentialType as Windows  -->  
      <!--for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="0f63d-112">服務原始程式碼已修改成可示範如何使用 <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> 存取呼叫者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="0f63d-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```  
  
 <span data-ttu-id="0f63d-113">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="0f63d-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0f63d-114">所呼叫的第一個方法 `GetCallerIdentity`，會將呼叫者身分識別的名稱傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="0f63d-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="0f63d-115">在主控台視窗中按 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="0f63d-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0f63d-116">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="0f63d-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0f63d-117">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0f63d-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0f63d-118">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="0f63d-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0f63d-119">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0f63d-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f63d-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f63d-120">See Also</span></span>
