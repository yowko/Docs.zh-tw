---
title: "HOW TO：設定最大時鐘誤差 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MaxClockSkew 屬性"
  - "WCF, 自訂繫結"
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# HOW TO：設定最大時鐘誤差
如果兩台電腦上的時鐘設定不相同，時間關鍵功能將脫離常軌。  若要降低這種可能性，您可以將 `MaxClockSkew` 屬性設定為 <xref:System.TimeSpan>。  此屬性可在兩種類別上使用：  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  重要：為了確保對談的安全性，在服務或用戶端啟動載入時，必須變更 `MaxClockSkew` 屬性的內容。  若要這麼做，必須設定 <xref:System.ServiceModel.Channels.SecurityBindingElement> \(由 <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>傳回\) 上的屬性。  
  
 若要變更其中一個系統提供繫結上的屬性，您必須在繫結集合中尋找安全性繫結項目，然後將 `MaxClockSkew` 屬性設定為新值。  衍生自 <xref:System.ServiceModel.Channels.SecurityBindingElement> 的兩個類別：<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 和 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>。  從集合上擷取安全性繫結時，您必須轉換至這些型別的其中一個型別以正確設定 `MaxClockSkew` 屬性。  下列範例使用運用 <xref:System.ServiceModel.WSHttpBinding> 的 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>。  如需指定在每個系統提供繫結中使用哪一種安全性繫結型別的清單，請參閱[系統提供的繫結](../../../../docs/framework/wcf/system-provided-bindings.md)。  
  
### 若要使用程式碼中的新時鐘扭曲值立自訂繫結  
  
1.  > [!WARNING]
    >  注意：在程式碼的下列命名空間中加入參考：<xref:System.ServiceModel.Channels>、<xref:System.ServiceModel.Description>、<xref:System.Security.Permissions> 及 <xref:System.ServiceModel.Security.Tokens>。  
  
     建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體，並將其安全性模式設定為 <xref:System.ServiceModel.SecurityMode>。  
  
2.  呼叫 <xref:System.ServiceModel.Channels.BindingElementCollection> 方法建立 <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> 類別的新執行個體。  
  
3.  使用 <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> 類別的 <xref:System.ServiceModel.Channels.BindingElementCollection> 方法尋找安全性繫結項目。  
  
4.  使用 <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> 方法時，轉換為實際型別。  下列範例轉換為 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 型別。  
  
5.  設定安全性繫結項目上的 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> 屬性。  
  
6.  使用適當的服務型別和基底位址建立 <xref:System.ServiceModel.ServiceHost>。  
  
7.  使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增端點並加入 <xref:System.ServiceModel.Channels.CustomBinding>。  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### 若要設定組態中的 MaxClockSkew  
  
1.  在 [\<繫結\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 元素區段中建立 [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。  
  
2.  建立 [\<繫結\>](../../../../docs/framework/misc/binding.md) 元素並將 `name` 屬性設定為適當值。  下列範例將它設定為 `MaxClockSkewBinding`。  
  
3.  新增編碼項目。  下列範例會新增 [\<textMessageEncoding\>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)。  
  
4.  新增 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)並對 `authenticationMode` 屬性進行適當的設定。  下列範例將屬性設定為 `Kerberos` 以說明該服務使用 Windows 驗證。  
  
5.  新增 [\<localServiceSettings\>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)並將 `maxClockSkew` 屬性設定為 `"##:##:##"` 形式的值。  下列範例將它設定為 7 分鐘。  選擇性地新增 [\<localServiceSettings\>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)並對 `maxClockSkew` 屬性進行適當的設定。  
  
6.  新增傳輸項目。  下列範例使用 [\<httpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)。  
  
7.  為了確保對談的安全性，[\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) 元素中進行啟動載入時，必須進行安全性設定。  
  
    ```  
  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    ```  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>   
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [HOW TO：使用 SecurityBindingElement 建立自訂繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)