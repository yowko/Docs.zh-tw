---
title: 模擬用戶端
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 29ed1f988819a47d8ac8845a379aeda5e15c655e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086462"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="ab377-102">模擬用戶端</span><span class="sxs-lookup"><span data-stu-id="ab377-102">Impersonating the Client</span></span>
<span data-ttu-id="ab377-103">此模擬範例會示範如何在服務端模擬呼叫者應用程式，以便讓服務能夠代表該呼叫者存取系統資源。</span><span class="sxs-lookup"><span data-stu-id="ab377-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="ab377-104">此樣本根據[自我裝載](../../../../docs/framework/wcf/samples/self-host.md)範例。</span><span class="sxs-lookup"><span data-stu-id="ab377-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="ab377-105">服務和用戶端設定檔的相同[自我裝載](../../../../docs/framework/wcf/samples/self-host.md)範例。</span><span class="sxs-lookup"><span data-stu-id="ab377-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab377-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="ab377-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ab377-107">此段服務程式碼已經過修改，使得服務的 `Add` 方法會使用 <xref:System.ServiceModel.OperationBehaviorAttribute> 模擬呼叫者，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ab377-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="ab377-108">因此，執行執行緒的安全性內容會在進入 `Add` 方法前切換成模擬呼叫者，然後在此方法結束時還原。</span><span class="sxs-lookup"><span data-stu-id="ab377-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="ab377-109">顯示於下列範例程式碼中的 `DisplayIdentityInformation` 方法，就是會顯示呼叫者身分識別的公用程式函式。</span><span class="sxs-lookup"><span data-stu-id="ab377-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",   
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 <span data-ttu-id="ab377-110">此服務的 `Subtract` 方法會使用命令式呼叫來模擬呼叫者，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ab377-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
```  
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
Console.WriteLine("Before impersonating");  
DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs   
            // on the system resource are enforced in the caller's context.   
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
Console.WriteLine("After reverting");  
DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="ab377-111">請注意，在這個範例中，並非整個呼叫期間都在模擬呼叫者，而只有在某些階段模擬。</span><span class="sxs-lookup"><span data-stu-id="ab377-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="ab377-112">一般來說，將模擬侷限在最小範圍比在整個作業都模擬來得好。</span><span class="sxs-lookup"><span data-stu-id="ab377-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="ab377-113">其他方法不會模擬呼叫者。</span><span class="sxs-lookup"><span data-stu-id="ab377-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="ab377-114">用戶端程式碼已修改成將模擬層級設定為 <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>。</span><span class="sxs-lookup"><span data-stu-id="ab377-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="ab377-115">用戶端會使用 <xref:System.Security.Principal.TokenImpersonationLevel> 列舉，指定服務要使用的模擬層級。</span><span class="sxs-lookup"><span data-stu-id="ab377-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="ab377-116">該列舉支援下列值：<xref:System.Security.Principal.TokenImpersonationLevel.None>、<xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>、<xref:System.Security.Principal.TokenImpersonationLevel.Identification>、<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> 和 <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>。</span><span class="sxs-lookup"><span data-stu-id="ab377-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="ab377-117">如果要在存取以 Windows ACL 保護之本機電腦上的系統資源時執行存取檢查，此模擬層級必須設定為 <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ab377-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="ab377-118">當您執行範例時，作業要求和回應會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="ab377-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ab377-119">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="ab377-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab377-120">服務必須使用系統管理帳戶執行，或是它執行的帳戶必須被授與註冊權限 `http://localhost:8000/ServiceModelSamples` 向 HTTP 層的 URI。</span><span class="sxs-lookup"><span data-stu-id="ab377-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="ab377-121">可以授與這類權限，藉由設定[命名空間保留區](https://go.microsoft.com/fwlink/?LinkId=95012)使用[Httpcfg.exe 工具](https://go.microsoft.com/fwlink/?LinkId=95010)。</span><span class="sxs-lookup"><span data-stu-id="ab377-121">Such rights can be granted by setting up a [Namespace Reservation](https://go.microsoft.com/fwlink/?LinkId=95012) using the [Httpcfg.exe tool](https://go.microsoft.com/fwlink/?LinkId=95010).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab377-122">在執行 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 的電腦上，只有在 Host.exe 應用程式擁有「模擬」權限的情況下才支援模擬 </span><span class="sxs-lookup"><span data-stu-id="ab377-122">On computers running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="ab377-123">(根據預設，只有系統管理員具有此權限)。若要新增此權限來執行服務的帳戶，請前往**系統管理工具**，開啟**本機安全性原則**，開啟**本機原則**，按一下  **使用者權限指派**，然後選取**驗證後模擬用戶端**，然後按兩下**屬性**，加入使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="ab377-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ab377-124">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="ab377-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ab377-125">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ab377-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ab377-126">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="ab377-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ab377-127">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ab377-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="ab377-128">若要示範此服務模擬呼叫者，請使用與執行服務之帳戶不同的帳戶執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="ab377-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="ab377-129">若要這麼做，請在命令提示字元輸入：</span><span class="sxs-lookup"><span data-stu-id="ab377-129">To do so, at the command prompt, type:</span></span>  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="ab377-130">接著，提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="ab377-130">You are then prompted for a password.</span></span> <span data-ttu-id="ab377-131">輸入先前指定帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="ab377-131">Enter the password for the account you previously specified.</span></span>  
  
5.  <span data-ttu-id="ab377-132">當您執行用戶端時，請注意用戶端在使用不同認證執行前後所具有的身分識別。</span><span class="sxs-lookup"><span data-stu-id="ab377-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab377-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab377-133">See Also</span></span>
