---
title: "&lt;nameEntry&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 507c71b5c13deeb7c1a81b6a4dd9604c3bd919f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltnameentrygt-element"></a>&lt;nameEntry&gt;項目
將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。  
  
 \<configuration>  
\<mscorlib >  
\<cryptographySettings >  
\<cryptoNameMapping >  
\<y >  
  
## <a name="syntax"></a>語法  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|**name**|必要屬性。<br /><br /> 指定密碼編譯類別實作的演算法的易記名稱。|  
|**class**|必要屬性。<br /><br /> 指定的值**名稱**屬性[ \<cryptoClass >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)項目。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.web`|指定 ASP.NET 組態區段的根項目。|  
  
## <a name="remarks"></a>備註  
 **名稱**屬性可以是抽象類別中找到的其中一個名稱<xref:System.Security.Cryptography>命名空間。 當您呼叫**建立**抽象的密碼編譯類別上的方法，抽象類別名稱傳遞至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>方法。 **CreateFromName**傳回所指定的類型的執行個體**類別**屬性。 如果**名稱**屬性是簡短名稱，例如 RSA，您可以使用該名稱呼叫時**CreateFromName**方法。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 **\<nameEntry >**項目參考加密編譯類別及設定執行階段。 您接著可以將字串"RSA"至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法和用法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>方法以傳回`MyCryptoRSAClass`物件。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [密碼編譯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [密碼編譯服務](../../../../../docs/standard/security/cryptographic-services.md)  
 [設定密碼編譯類別](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
