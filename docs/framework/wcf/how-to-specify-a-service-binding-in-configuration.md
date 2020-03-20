---
title: HOW TO：指定組態中的服務繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 245fe50ed5a80c51163652defb642cebefd55dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184025"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>HOW TO：指定組態中的服務繫結
在此範例中會定義基本計算機服務的 `ICalculator` 合約，該服務會在 `CalculatorService` 類別中實作，然後會在 Web.config 檔案中設定其端點，其中會指定服務使用 <xref:System.ServiceModel.BasicHttpBinding>。 有關如何使用代碼而不是配置配置配置此服務的說明，請參閱[：在代碼 中指定服務綁定](how-to-specify-a-service-binding-in-code.md)。  
  
 通常最佳作法是在組態中以宣告方式指定繫結和位址資訊，而不是在程式碼中強制指定。 在程式碼中定義端點通常不太實用，因為部署之服務的繫結和位址通常與開發服務時所使用的繫結和位址不同。 比較一般性的作法是將繫結和位址資訊留在程式碼外面，如此一來，不需要重新編譯或重新部署應用程式，就可以變更繫結和位址資訊。  
  
 可以使用[配置編輯器工具 （SvcConfigEditor.exe）](configuration-editor-tool-svcconfigeditor-exe.md)執行以下所有配置步驟。  
  
 有關此示例的源副本，請參閱[基本綁定](./samples/basicbinding.md)。  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>指定用來設定服務的 BasicHttpBinding  
  
1. 定義服務類型的服務合約。  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. 在服務類別中實作服務合約。  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > 此服務的實作中不會指定位址或繫結資訊。 同時，您不需要撰寫可從組態檔擷取該資訊的程式碼。  
  
3. 請建立 Web.config 檔，為使用 `CalculatorService` 的 <xref:System.ServiceModel.WSHttpBinding> 設定端點。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  

            <!-- Leave the address blank to be populated by default -->
            <!-- from the hosting environment,in this case IIS, so -->
            <!-- the address will just be that of the IIS Virtual -->
            <!-- Directory. -->

            <!-- Specify the binding configuration name for that -->
            <!-- binding type. This is optional but useful if you -->
            <!-- want to modify the properties of the binding. -->
            <!-- The bindingConfiguration name Binding1 is defined -->
            <!-- below in the bindings element. -->
            <endpoint
                address=""
                binding="wsHttpBinding"  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. 請建立 Service.svc 檔，其中包含下列這行文字，並且將它放入 Internet Information Services (IIS) 虛擬目錄中。  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a>若要修改繫結屬性的預設值  
  
1. 要修改 的一個預設屬性值<xref:System.ServiceModel.WSHttpBinding>，請在其[\<wsHttpBinding](../configure-apps/file-schema/wcf/wshttpbinding.md)>`<binding name="Binding1">`元素中創建新的綁定配置名稱 ，並為此繫結元素中綁定的屬性設置新值。 例如，若要將預設的開啟和關閉逾時值從 1 分鐘變更為 2 分鐘，請將下列文字加入至組態檔。  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>另請參閱

- [使用繫結設定服務與用戶端](using-bindings-to-configure-services-and-clients.md)
- [指定端點位址](specifying-an-endpoint-address.md)
