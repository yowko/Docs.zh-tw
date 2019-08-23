---
title: 模擬用戶端
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 61befdcaf1381120dba6f72ba592dade09d0490a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968333"
---
# <a name="impersonating-the-client"></a>模擬用戶端
此模擬範例會示範如何在服務端模擬呼叫者應用程式，以便讓服務能夠代表該呼叫者存取系統資源。  
  
 這個範例是以[自我裝載](../../../../docs/framework/wcf/samples/self-host.md)範例為基礎。 服務和用戶端設定檔與[自我裝載](../../../../docs/framework/wcf/samples/self-host.md)範例的檔案相同。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此段服務程式碼已經過修改，使得服務的 `Add` 方法會使用 <xref:System.ServiceModel.OperationBehaviorAttribute> 模擬呼叫者，如下列範例程式碼所示。  
  
```csharp
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
  
 因此，執行執行緒的安全性內容會在進入 `Add` 方法前切換成模擬呼叫者，然後在此方法結束時還原。  
  
 顯示於下列範例程式碼中的 `DisplayIdentityInformation` 方法，就是會顯示呼叫者身分識別的公用程式函式。  
  
```csharp
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
  
 此服務的 `Subtract` 方法會使用命令式呼叫來模擬呼叫者，如下列範例程式碼所示。  
  
```csharp
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
  
 請注意，在這個範例中，並非整個呼叫期間都在模擬呼叫者，而只有在某些階段模擬。 一般來說，將模擬侷限在最小範圍比在整個作業都模擬來得好。  
  
 其他方法不會模擬呼叫者。  
  
 用戶端程式碼已修改成將模擬層級設定為 <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>。 用戶端會使用 <xref:System.Security.Principal.TokenImpersonationLevel> 列舉，指定服務要使用的模擬層級。 該列舉支援下列值：<xref:System.Security.Principal.TokenImpersonationLevel.None>、<xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>、<xref:System.Security.Principal.TokenImpersonationLevel.Identification>、<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> 和 <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>。 如果要在存取以 Windows ACL 保護之本機電腦上的系統資源時執行存取檢查，此模擬層級必須設定為 <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>，如下列範例程式碼所示。  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 當您執行範例時，作業要求和回應會顯示在服務與用戶端主控台視窗中。 在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。  
  
> [!NOTE]
> 服務必須使用系統管理帳戶執行，或是它執行的帳戶必須被授與註冊權限 `http://localhost:8000/ServiceModelSamples` 向 HTTP 層的 URI。 您可以使用[HTTPcfg.exe](https://go.microsoft.com/fwlink/?LinkId=95010)來設定[命名空間保留](https://go.microsoft.com/fwlink/?LinkId=95012)區, 以授與這類許可權。  
  
> [!NOTE]
> 在執行 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 的電腦上，只有在 Host.exe 應用程式擁有「模擬」權限的情況下才支援模擬 (根據預設，只有系統管理員具有此權限)。若要將此許可權新增至服務執行身分的帳戶, 請移至 [系統**管理工具**], 開啟 [**本機安全性原則**], 開啟 [**本機原則**], 按一下 [**使用者權限指派**], 然後選取 [**之後模擬用戶端]驗證**, 然後按兩下 [**屬性**] 以新增使用者或群組。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
4. 若要示範此服務模擬呼叫者，請使用與執行服務之帳戶不同的帳戶執行用戶端。 若要這麼做，請在命令提示字元輸入：  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     接著，提示您輸入密碼。 輸入先前指定帳戶的密碼。  
  
5. 當您執行用戶端時，請注意用戶端在使用不同認證執行前後所具有的身分識別。  
