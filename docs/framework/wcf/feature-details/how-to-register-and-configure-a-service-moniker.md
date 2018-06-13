---
title: HOW TO：註冊和設定服務 Moniker
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 1d245327c1e7d53de9a88c93ff0399d8e231a1df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493310"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>HOW TO：註冊和設定服務 Moniker
之前使用型別之合約的 COM 應用程式中的 Windows Communication Foundation (WCF) 服務 moniker，您必須向 COM 註冊必要的屬性的類型，並使用必要的繫結設定 COM 應用程式和 moniker組態設定。  
  
### <a name="to-register-the-required-attributed-types-with-com"></a>使用 COM 註冊必要的屬性化型別  
  
1.  使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具，可從 WCF 服務擷取中繼資料合約。 這會原始程式碼產生 WCF 用戶端組件和用戶端應用程式組態檔。  
  
2.  請確定組件中的型別已標示為 `ComVisible`。 若要這樣做，請在 Visual Studio 專案中將下列屬性新增至 AssemblyInfo.cs 檔。  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  編譯 managed 的 WCF 用戶端，做為強式名稱組件。 這樣做將需要以密碼金鑰組 (Key Pairs) 進行簽署。 如需詳細資訊，請參閱[簽署以強式名稱組件](http://go.microsoft.com/fwlink/?LinkId=94874).NET 開發人員指南中。  
  
4.  使用組件註冊 (Regasm.exe) 工具並搭配 `/tlb` 選項，以使用 COM 註冊組件中的型別。  
  
5.  使用全域組件快取 (Gacutil.exe) 工具，將組件新增至全域組件快取中。  
  
    > [!NOTE]
    >  簽署組件並將該組件新增至全域組件快取都是選用性步驟，但這兩個步驟可以簡化在執行階段時，從正確的位置載入組件的程序。  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>使用必要的繫結組態設定 COM 應用程式和 Moniker  
  
-   將繫結定義 (所產生[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)產生的用戶端應用程式組態檔中) 用戶端應用程式組態檔中。 例如，若是名稱為 CallCenterClient.exe 的 Visual Basic 6.0 可執行檔，應該將組態放置在與可執行檔相同之目錄內的 CallCenterConfig.exe.config 檔案中。 用戶端應用程式現在就可使用 Moniker。 請注意，如果使用其中一種標準繫結 WCF 所提供的類型，不需要繫結組態。  
  
     接著會註冊下列型別。  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     已使用 `wsHttpBinding` 繫結公開應用程式。 針對提供的型別和應用程式組態，將會使用下列範例 Moniker 字串。  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     在將參考新增至包含 `IMathService` 型別的組件之後，您就可以從 Visual Basic 6.0 應用程式中使用這些 Moniker 字串，如下列範例程式碼所示。  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     在這個範例中，針對用戶端應用程式將繫結組態 `Binding1` 的定義存放在適當命名的組態檔中，例如 vb6appname.exe.config。  
  
    > [!NOTE]
    >  您可以在 C#、C++ 或其他 .NET 語言應用程式中使用類似的程式碼。  
  
    > [!NOTE]
    >  ：如果 Moniker 的格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。 如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。  
  
     雖然本主題著重於從 VB 6.0 程式碼中使用服務 Moniker，但您也可以使用其他語言中的服務 Moniker。 從 C++ 程式碼中使用 Moniker 時，應該以 "no_namespace named_guids raw_interfaces_only" 這個名稱匯入 Svcutil.exe 產生的組件，如下列程式碼所示。  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     這樣會修改匯入的介面定義，讓所有方法都會傳回 `HResult`。 其他傳回值都會轉換為 Out 參數。 整體的執行方法仍然相同。 這樣可讓您在 Proxy 上呼叫方法時，判斷發生例外狀況的原因。 不過這個功能只能用於 C++ 程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
