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
ms.openlocfilehash: 1bb5c6b46ff0f75082b0b7b631a197dd64156cf9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672860"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>對應物件識別項至密碼編譯演算法
數位簽章確認，資料未遭竄改時每個程式傳送到另一個。 通常透過將數學函式套用至要簽署之資料的雜湊計算數位簽章。 格式化時必須經過簽署的雜湊值，有些數位簽章演算法就會附加在格式化作業 ASN.1 物件識別碼 (OID)。 OID 識別用來計算雜湊演算法。 您可以將演算法對應至物件識別碼，若要擴充的密碼編譯機制，來使用自訂的演算法。 下列範例示範如何將物件識別項對應至新的雜湊演算法。  
  
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
  
 [ \<OidEntry > 項目](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)包含兩個屬性。 **OID**屬性是物件識別碼數字。 **名稱**屬性是值**名稱**屬性從[ \<nameEntry > 項目](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)。 物件識別元可以對應至簡單名稱之前，必須是將演算法名稱對應至類別。  
  
## <a name="see-also"></a>另請參閱
- [設定密碼編譯類別](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [The signature is valid](../../../docs/standard/security/cryptographic-services.md)
