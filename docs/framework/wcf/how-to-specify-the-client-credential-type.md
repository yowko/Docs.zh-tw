---
title: "HOW TO：指定用戶端認證類型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安全性認證, 新增至 SOAP 訊息"
  - "WCF, 安全性"
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HOW TO：指定用戶端認證類型
在設定過安全性模式 \(傳輸或訊息\) 後，您就會擁有設定用戶端認證類型的選項。這個屬性會指定用戶端必須向服務提供何種類型認證來進行驗證。[!INCLUDE[crabout](../../../includes/crabout-md.md)]設定安全性模式 \(在設定用戶端認證類型之前的必要步驟\) 的詳細資訊，請參閱 [HOW TO：設定安全性模式](../../../docs/framework/wcf/how-to-set-the-security-mode.md)。  
  
### 透過程式碼設定用戶端認證類型  
  
1.  建立服務將會使用之繫結的執行個體。這個範例會使用 <xref:System.ServiceModel.WSHttpBinding> 繫結。  
  
2.  將 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> 屬性設定為適當值。這個範例會使用訊息模式。  
  
3.  將 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> 屬性設定為適當值。這個範例會將該屬性設定為使用 Windows 驗證 \(<xref:System.ServiceModel.MessageCredentialType>\)。  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### 透過組態設定用戶端認證類型  
  
1.  將 [\<system.serviceModel\>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 項目新增到組態檔中。  
  
2.  將 [\<繫結\>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 項目新增為子項目。  
  
3.  新增適當的繫結。這個範例會使用 [\<wsHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 項目。  
  
4.  新增 [\<繫結\>](../../../docs/framework/misc/binding.md) 項目，並將 `name` 屬性設定為適當值。這個範例會使用 "SecureBinding" 的名稱。  
  
5.  新增 `<security>` 繫結。將 `mode` 屬性設定為適當值。這個範例會將其設定為 `"Message"`。  
  
6.  根據安全性模式，新增 `<message>` 或 `<transport>` 項目。將 `clientCredentialType` 屬性設定為適當值。這個範例會使用 `"Windows"`。  
  
    ```  
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
  
## 請參閱  
 [保護服務的安全](../../../docs/framework/wcf/securing-services.md)   
 [HOW TO：設定安全性模式](../../../docs/framework/wcf/how-to-set-the-security-mode.md)