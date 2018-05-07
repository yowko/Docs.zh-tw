---
title: HOW TO：指定組態中的用戶端繫結
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: e2ea5a4b1c2ca9b661be5d4c653a3b5668bd26f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>HOW TO：指定組態中的用戶端繫結
在此範例中，建立了一個使用計算機服務的用戶端主控台應用程式，並在組態中以宣告方式指定用戶端的繫結。 用戶端會存取 `CalculatorService` (該服務會實作 `ICalculator` 介面)，而服務和用戶端都會使用 <xref:System.ServiceModel.BasicHttpBinding> 類別。  
  
 所述的程序假設計算機服務正在執行中。 如需如何建置服務資訊，請參閱[How to： 在組態中指定服務繫結](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。 它也會使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Windows Communication Foundation (WCF) 提供自動產生的用戶端元件。 此工具會產生用戶端程式碼，以及存取服務的組態。  
  
 用戶端會建置成兩個部分。 Svcutil.exe 會產生 `ClientCalculator`，而該元件會實作 `ICalculator` 介面。 接著會藉由建構 `ClientCalculator` 的執行個體，以建構此用戶端應用程式。  
  
 通常最佳作法是在組態中以宣告方式指定繫結和位址資訊，而不是在程式碼中強制指定。 在程式碼中定義端點通常不太實用，因為部署之服務的繫結和位址通常與開發服務時所使用的繫結和位址不同。 比較一般性的作法是將繫結和位址資訊留在程式碼外面，如此一來，不需要重新編譯或重新部署應用程式，就可以變更繫結和位址資訊。  
  
 您可以執行下列組態步驟的所有使用[組態編輯器工具 (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。  
  
 此範例的來源副本，請參閱[BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md)範例。  
  
### <a name="specifying-a-client-binding-in-configuration"></a>指定組態中的用戶端繫結  
  
1.  從命令列使用 Svcutil.exe 產生取自服務中繼資料的程式碼。  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  所產生的用戶端會包含 `ICalculator` 介面，其中定義了用戶端實作所必須滿足的服務合約。  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  產生的用戶端也會包含 `ClientCalculator` 的實作。  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  Svcutil.exe 也會為使用 <xref:System.ServiceModel.BasicHttpBinding> 類別的用戶端產生組態。 當使用 Visual Studio，請將這個檔案 App.config 命名。請注意，服務的實作內部並未指定位址和繫結資訊。 同時，您不需要撰寫可從組態檔擷取該資訊的程式碼。  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5.  在應用程式內建立 `ClientCalculator` 的執行個體，然後呼叫服務作業。  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  請編譯並執行用戶端。  
  
## <a name="see-also"></a>另請參閱  
 [使用繫結設定服務與用戶端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
