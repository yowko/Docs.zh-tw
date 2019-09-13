---
title: 作法：在沙箱中執行部分信任的程式碼
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8b1db291fbaf19ae9086fe1e2b76a475d198e19
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894556"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>作法：在沙箱中執行部分信任的程式碼
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 沙箱是指在受限制的安全性環境中執行程式碼的做法，這會限制授與程式碼的存取權限。 例如，如果您有來自不完全信任來源的 Managed 程式庫，則不應該以完全信任的方式執行。 相反地，您應該將程式碼放在沙箱，限制其權限為您所預期它會需要的權限 (例如，<xref:System.Security.Permissions.SecurityPermissionFlag.Execution> 權限)。  
  
 您也可以使用沙箱來測試您將散發的程式碼，該程式碼將在部分信任環境中執行。  
  
 <xref:System.AppDomain> 是提供沙箱給 Managed 應用程式的有效方式。 用來執行部分信任程式碼的應用程式定義域具有權限，於 <xref:System.AppDomain> 中執行時，會定義可以使用的受保護資源。 在 <xref:System.AppDomain> 內部執行的程式碼會由與 <xref:System.AppDomain> 相關聯的權限繫結，並且僅允許存取指定的資源。 <xref:System.AppDomain> 也包含 <xref:System.Security.Policy.StrongName> 陣列，用來識別要以完全信任方式載入的組件。 這可讓 <xref:System.AppDomain> 的建立者啟動新的沙箱定義域，可允許特定協助程式組件變成完全信任。 另一個以完全信任方式載入組件的選項為將它們放在全域組件快取中；不過，這會在該電腦上建立的應用程式定義域中以完全信任方式載入所有組件。 強式名稱的清單支援針對每個 <xref:System.AppDomain> 的決策，這會提供更嚴格的判斷。  
  
 您可以使用 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> 方法多載來指定在沙箱中執行的應用程式之權限集。 這個多載可讓您指定您想要的程式碼存取安全性之確切層級。 使用這個多載來載入至 <xref:System.AppDomain> 的組件可以只具有指定的授權集，或者可以是完全信任的。 如果組件位於全域組件快取中或在 `fullTrustAssemblies` (<xref:System.Security.Policy.StrongName>) 陣列參數中列出，則會授與組件完全信任。 只應加入已知為完全信任的組件至 `fullTrustAssemblies` 清單。  
  
 此多載具有下列簽章：  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> 方法多載的參數會指定 <xref:System.AppDomain> 的名稱、<xref:System.AppDomain> 的辨識項、會指定沙箱之應用程式基底的 <xref:System.AppDomainSetup> 物件、要使用的授權集，以及完全信任組件的強式名稱。  
  
 基於安全性理由，`info` 參數中指定的應用程式基底不能為裝載應用程式的應用程式基底。  
  
 對於 `grantSet` 參數，您可以指定已明確建立的權限集合或 <xref:System.Security.SecurityManager.GetStandardSandbox%2A> 方法所建立的標準權限集。  
  
 不同於大部分 <xref:System.AppDomain> 的載入，<xref:System.AppDomain> 辨識項 (由 `securityInfo` 參數所提供) 不用來為部分信任的組件判斷授權集。 相反地，它由 `grantSet` 參數獨立指定。 不過，辨識項可以用於其他用途，例如判斷隔離儲存區的範圍。  
  
### <a name="to-run-an-application-in-a-sandbox"></a>在沙箱中執行應用程式  
  
1. 建立要授與給不受信任的應用程式之授權集。 您可以授與的最小權限是 <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> 權限。 您也可授與其他您認為對不受信任的程式碼可能安全的權限；例如 <xref:System.Security.Permissions.IsolatedStorageFilePermission>。 下列程式碼會建立新的權限集合，其中只有 <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> 權限。  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     或者，您可以使用現有的具名使用權限集合，例如網際網路。  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <xref:System.Security.SecurityManager.GetStandardSandbox%2A> 方法會根據在辨識項中的區域傳回 `Internet` 權限集合或 `LocalIntranet` 權限集合。 對於某些做為參考傳遞的辨識項物件，<xref:System.Security.SecurityManager.GetStandardSandbox%2A> 也會建構其識別權限。  
  
2. 簽署包含裝載類別 (在此範例中名為 `Sandboxer`) 的組件，該類別會呼叫不受信任的程式碼。 加入 <xref:System.Security.Policy.StrongName>，這會用來簽署組件給 <xref:System.AppDomain.CreateDomain%2A> 呼叫的 `fullTrustAssemblies` 參數之 <xref:System.Security.Policy.StrongName> 陣列。 裝載的類別必須以完全信任方式執行，以啟用部分信任程式碼的執行，或提供服務給部分信任應用程式。 這就是您讀取組件 <xref:System.Security.Policy.StrongName> 的方式。  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     .NET Framework 組件，例如 mscorlib 和 System.dll 就不必加入完全信任清單，因為它們會以完全信任方式從全域組件快取中載入。  
  
3. 初始化 <xref:System.AppDomain.CreateDomain%2A> 方法的 <xref:System.AppDomainSetup> 參數。 使用這個參數，您可以控制許多新的 <xref:System.AppDomain> 設定。 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性是重要的設定，而且應該不同於裝載應用程式的 <xref:System.AppDomain> 之 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性。 如果 <xref:System.AppDomainSetup.ApplicationBase%2A> 設定相同，則部分信任應用程式可取得裝載的應用程式，以載入 (以完全信任方式) 它所定義的例外狀況，因而加以利用。 這是為什麼不建議使用 catch (例外狀況) 的另一個原因。 將主機的應用程式基底設定為不同於沙箱應用程式的應用程式基底，可減少惡意探索的風險。  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. 呼叫 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> 方法多載來使用我們已指定的參數建立應用程式定義域。  
  
     此方法的簽章是：  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     其他資訊：  
  
    - 這是採用 <xref:System.Security.PermissionSet> 做為參數的 <xref:System.AppDomain.CreateDomain%2A> 方法之唯一多載，因此也是讓您在部分信任設定中載入應用程式的唯一多載。  
  
    - `evidence` 參數不用來計算權限集合；它由 .NET Framework 的其他功能用來進行識別。  
  
    - 設定 `info` 參數的 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性對於這個多載而言是強制的。  
  
    - `fullTrustAssemblies` 參數具有 `params` 關鍵字，這表示不需要建立 <xref:System.Security.Policy.StrongName> 陣列。 允許將 0、1 或更多的強式名稱當做參數傳遞。  
  
    - 若要建立應用程式定義域的程式碼是：  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. 將程式碼載入您所建立的沙箱 <xref:System.AppDomain> 中。 有兩種方法可以達到這個目的：  
  
    - 呼叫組件的 <xref:System.AppDomain.ExecuteAssembly%2A> 方法。  
  
    - 使用 <xref:System.Activator.CreateInstanceFrom%2A> 方法在新的 <xref:System.AppDomain> 建立衍生自 <xref:System.MarshalByRefObject> 類別的執行個體。  
  
     第二種方法更合適，因為它讓您更輕鬆地將參數傳遞給新的 <xref:System.AppDomain> 執行個體。 <xref:System.Activator.CreateInstanceFrom%2A> 方法提供兩個重要功能：  
  
    - 您可使用會指向不包含組件位置的程式碼基底。  
  
    - 您可以在 <xref:System.Security.CodeAccessPermission.Assert%2A> 之下建立完全信任 (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>)，這可讓您建立關鍵類別的執行個體。 (每當您的組件不具有透明度標記，且以完全信任方式載入時就會發生)。因此您應特別小心，只能建立您信任此函式的程式碼，我們建議您在新的應用程式定義域中只建立完全信任類別的執行個體。  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     請注意若要在新的定義域中建立類別的執行個體，此類別必須擴充 <xref:System.MarshalByRefObject> 類別  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. 解除包裝新定義域之執行個體至此定義域的參考。 這個參考用來執行不受信任的程式碼。  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. 請在您剛建立的 `Sandboxer` 類別之執行個體中呼叫 `ExecuteUntrustedCode` 方法。  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     這個呼叫會在沙箱應用程式定義域中執行，具有受限制的使用權限。  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is   
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <xref:System.Reflection> 用來在部分信任組件中取得方法的控制代碼。 控制代碼可用來以安全的方式搭配最小權限執行程式碼。  
  
     在先前的程式碼中，請先注意完全信任權限的 <xref:System.Security.PermissionSet.Assert%2A>，然後才列印 <xref:System.Security.SecurityException>。  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     完全信任的判斷提示用來從 <xref:System.Security.SecurityException> 取得擴充的資訊。 在沒有 <xref:System.Security.PermissionSet.Assert%2A> 的情況下，<xref:System.Security.SecurityException> 的 <xref:System.Security.SecurityException.ToString%2A> 方法會在堆疊上探索部分信任程式碼，並且限制傳回的資訊。 如果部分信任程式碼可能讀取該資訊，則這可能會造成安全性問題，但不授與 <xref:System.Security.Permissions.UIPermission> 可降低風險。 應該謹慎使用完全信任的判斷提示，而且僅當您確定不允許部分信任程式碼提升為完全信任時才能使用。 在相同的函式中，以及為了完全信任而呼叫判斷提示之後，通常請不要呼叫您不信任的程式碼。 當您使用完畢後，一律將判斷提示還原會是最佳的做法。  
  
## <a name="example"></a>範例  
 下列範例會實作上一節中的程序。 在此範例中，Visual Studio 方案裡名為 `Sandboxer` 的專案還包含一個名為 `UntrustedCode` 的專案，這會實作 `UntrustedClass` 類別。 此案例假定您已下載包含方法的程式庫組件，該方法預期會傳回 `true` 或 `false` 來指出您提供的數字是否為費式數列。 相反地，該方法會嘗試從您的電腦讀取檔案。 下列範例顯示未受信任的程式碼。  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 下列範例顯示執行不受信任程式碼的 `Sandboxer` 應用程式之程式碼。  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another   
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder   
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to   
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.   
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the   
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are   
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../standard/security/secure-coding-guidelines.md)
