---
title: 對應物件識別項至密碼編譯演算法
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7801c55cf6b3334347788013d9052038d5d2f3ec
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756614"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>對應物件識別項至密碼編譯演算法
數位簽章確認，資料未遭竄改時每個程式傳送到另一個。 通常就是透過將數學函式套用至要簽署資料的雜湊計算數位簽章。 格式化時要簽署的雜湊值，有些數位簽章演算法就會附加在格式化作業的一部分 ASN.1 物件識別碼 (OID)。 OID 識別用來計算雜湊演算法。 您可以將演算法對應至物件識別碼，來擴充要使用的自訂演算法的新一代密碼編譯機制。 下列範例會示範如何將物件識別碼對應至新的雜湊演算法。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 [ \<OidEntry > 項目](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)包含兩個屬性。 **OID**屬性是物件識別碼。 **名稱**屬性是值**名稱**屬性從[ \<y > 項目](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)。 物件識別元可以對應至簡單名稱之前，必須是從演算法名稱對應至類別。  
  
## <a name="see-also"></a>另請參閱  
 [設定密碼編譯類別](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [The signature is valid](../../../docs/standard/security/cryptographic-services.md)
