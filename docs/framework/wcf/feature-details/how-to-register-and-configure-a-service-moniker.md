---
title: "HOW TO：註冊和設定服務 Moniker | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "COM [WCF], 設定服務 Moniker"
  - "COM [WCF], 註冊服務 Moniker"
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# HOW TO：註冊和設定服務 Moniker
在具有型別之合約的 COM 應用程式中使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務 Moniker 之前，您必須使用 COM 註冊必要的屬性化型別，並以必要的繫結組態設定 COM 應用程式和 Moniker。  
  
### 使用 COM 註冊必要的屬性化型別  
  
1.  使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 工具以從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務擷取中繼資料合約。  這樣做會產生 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端組件的原始程式碼和用戶端應用程式組態檔。  
  
2.  請確定組件中的型別已標示為 `ComVisible`。  若要這樣做，請在 Visual Studio 專案中將下列屬性新增至 AssemblyInfo.cs 檔。  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  將 Managed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端編譯為強式名稱的組件。  這樣做將需要以密碼金鑰組 \(Key Pairs\) 進行簽署。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] 《.NET 開發人員手冊》中的[以強式名稱簽署組件](http://go.microsoft.com/fwlink/?LinkId=94874)。  
  
4.  使用組件註冊 \(Regasm.exe\) 工具並搭配 `/tlb` 選項，以使用 COM 註冊組件中的型別。  
  
5.  使用全域組件快取 \(Gacutil.exe\) 工具，將組件新增至全域組件快取中。  
  
    > [!NOTE]
    >  簽署組件並將該組件新增至全域組件快取都是選用性步驟，但這兩個步驟可以簡化在執行階段時，從正確的位置載入組件的程序。  
  
### 使用必要的繫結組態設定 COM 應用程式和 Moniker  
  
-   將繫結定義 \(由產生之用戶端應用程式組態檔中的 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 所產生\) 放置在用戶端應用程式的組態檔中。  例如，若是名稱為 CallCenterClient.exe 的 Visual Basic 6.0 可執行檔，應該將組態放置在與可執行檔相同之目錄內的 CallCenterConfig.exe.config 檔案中。  用戶端應用程式現在就可使用 Moniker。  請注意，如果使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供的其中一種標準繫結型別，則不需要繫結組態。  
  
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
  
     已使用 `wsHttpBinding` 繫結公開應用程式。  針對提供的型別和應用程式組態，將會使用下列範例 Moniker 字串。  
  
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
    >  您可以在 C\#、C\+\+ 或其他 .NET 語言應用程式中使用類似的程式碼。  
  
    > [!NOTE]
    >  ：如果 Moniker 的格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。  如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。  
  
     雖然本主題著重於從 VB 6.0 程式碼中使用服務 Moniker，但您也可以使用其他語言中的服務 Moniker。  從 C\+\+ 程式碼中使用 Moniker 時，應該以 "no\_namespace named\_guids raw\_interfaces\_only" 這個名稱匯入 Svcutil.exe 產生的組件，如下列程式碼所示。  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     這樣會修改匯入的介面定義，讓所有方法都會傳回 `HResult`。  其他傳回值都會轉換為 Out 參數。  整體的執行方法仍然相同。  這樣可讓您在 Proxy 上呼叫方法時，判斷發生例外狀況的原因。  不過這個功能只能用於 C\+\+ 程式碼。  
  
## 請參閱  
 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)