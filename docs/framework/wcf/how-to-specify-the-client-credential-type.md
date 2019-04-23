---
title: HOW TO：指定用戶端認證類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: 775c6a297047c7a0e16db091f9a22686fdb01efb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339394"
---
# <a name="how-to-specify-the-client-credential-type"></a>HOW TO：指定用戶端認證類型
在設定過安全性模式 (傳輸或訊息) 後，您就會擁有設定用戶端認證類型的選項。 這個屬性會指定用戶端必須提供給服務以進行驗證的認證類型。 如需有關如何設定安全性模式 （在設定用戶端認證類型之前的必要步驟） 的詳細資訊，請參閱[How to:設定安全性模式](../../../docs/framework/wcf/how-to-set-the-security-mode.md)。  
  
### <a name="to-set-the-client-credential-type-in-code"></a>透過程式碼設定用戶端認證類型  
  
1. 建立服務將會使用之繫結的執行個體。 這個範例會使用 <xref:System.ServiceModel.WSHttpBinding> 繫結。  
  
2. 將 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> 屬性設定為適當值。 這個範例會使用訊息模式。  
  
3. 將 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> 屬性設定為適當值。 這個範例會將該屬性設定為使用 Windows 驗證 (<xref:System.ServiceModel.MessageCredentialType.Windows>)。  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>透過組態設定用戶端認證類型  
  
1. 新增[ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)至組態檔的項目。  
  
2. 做為子項目中，新增[\<繫結 >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)項目。  
  
3. 新增適當的繫結。 這個範例會使用[ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目。  
  
4. 新增[\<繫結 >](../../../docs/framework/misc/binding.md)項目並將`name`屬性設為適當的值。 這個範例會使用 "SecureBinding" 的名稱。  
  
5. 新增 `<security>` 繫結。 將 `mode` 屬性設定為適當值。 這個範例會將其設定為 `"Message"`。  
  
6. 根據安全性模式，新增 `<message>` 或 `<transport>` 項目。 將 `clientCredentialType` 屬性設定為適當值。 這個範例會使用 `"Windows"`。  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a>另請參閱

- [保護服務安全](../../../docs/framework/wcf/securing-services.md)
- [如何：設定安全性模式](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
