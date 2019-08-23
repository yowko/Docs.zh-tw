---
title: 作法：建立使用自訂憑證驗證程式的服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: 156d661fd5602333fae8066f3062b442a1df19af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951699"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>作法：建立使用自訂憑證驗證程式的服務
這個主題將示範如何實作自訂憑證驗證程式，以及如何設定用戶端或服務認證，以使用自訂憑證驗證程式來取代預設的憑證驗證邏輯。  
  
 如果使用 x.509 憑證來驗證用戶端或服務, Windows Communication Foundation (WCF) 預設會使用 Windows 憑證存放區和密碼編譯 API 來驗證憑證, 並確保它是受信任的。 有時內建的憑證驗證功能不足，必須變更。 WCF 藉由允許使用者新增自訂憑證驗證程式, 提供簡單的方式來變更驗證邏輯。 如果指定了自訂憑證驗證程式, WCF 不會使用內建的憑證驗證邏輯, 而會改為依賴自訂驗證程式。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-create-a-custom-certificate-validator"></a>建立自訂憑證驗證程式  
  
1. 定義衍生自 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 的新類別。  
  
2. 實作抽象的 <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> 方法。 必須驗證的憑證會傳遞為方法的引數。 如果根據驗證邏輯，傳遞的憑證是無效的，這個方法會擲回 <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>。 如果憑證是有效的，方法會傳回至呼叫者。  
  
    > [!NOTE]
    > 若要將驗證錯誤傳回至用戶端，請在 <xref:System.ServiceModel.FaultException> 方法中擲回 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>。  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>在服務組態中指定自訂憑證驗證程式  
  
1. 將行為 > 元素和[ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)新增至[ \<system.servicemodel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)元素。 [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
2. `name` [新增\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)並將屬性設定為適當的值。  
  
3. 將 serviceCredentials > 新增至元素。`<behavior>` [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)  
  
4. 將 `<clientCertificate>` 項目加入至 `<serviceCredentials>` 項目。  
  
5. 將驗證 > 新增至元素。`<clientCertificate>` [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
  
6. 將 `customCertificateValidatorType` 屬性設定為驗證程式類型。 下列範例會將屬性設定為類型的命名空間和名稱。  
  
7. 將 `certificateValidationMode` 屬性設定為 `Custom`。  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>使用用戶端上的組態來指定自訂憑證驗證程式  
  
1. 將行為 > 元素和[ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)新增至[ \<system.servicemodel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)元素。 [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
2. 新增 endpointBehaviors [ >元素。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)  
  
3. 加入 `<behavior>` 項目，並將 `name` 屬性設定為適當值。  
  
4. 新增 clientCredentials [ >元素。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
  
5. 新增 serviceCertificate [ >\< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)。  
  
6. 新增驗證[ >,如下列範例所示。\< ](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
7. 將 `customCertificateValidatorType` 屬性設定為驗證程式類型。  
  
8. 將 `certificateValidationMode` 屬性設定為 `Custom`。 下列範例會將屬性設定為類型的命名空間和名稱。  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"   
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>使用服務上的程式碼來指定自訂憑證驗證程式  
  
1. 請在 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> 屬性上指定自訂憑證驗證程式。 您可以使用 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 屬性來存取服務認證。  
  
2. 將 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> 屬性設定為 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>。  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>使用用戶端上的程式碼來指定自訂憑證驗證程式  
  
1. 請使用 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> 屬性來指定自訂憑證驗證程式。 您可以使用 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 屬性來存取用戶端認證。 (由[system.servicemodel 中繼資料公用程式工具 (Svcutil)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)所產生的用戶端類別一律衍生<xref:System.ServiceModel.ClientBase%601>自類別)。  
  
2. 將 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> 屬性設定為 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 下列範例將示範在服務上實作自訂憑證驗證程式及其使用方式。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
