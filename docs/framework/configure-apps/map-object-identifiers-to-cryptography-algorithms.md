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
ms.openlocfilehash: a5aebac2d392d4540581dfe7c7afff0819968ac0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912548"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>對應物件識別項至密碼編譯演算法
數位簽章可確保資料從某個程式傳送至另一個程式時, 不會遭到篡改。 通常數位簽章的計算方式是將數學函式套用到要簽署的資料雜湊。 格式化要簽署的雜湊值時, 某些數位簽章演算法會在格式化作業中附加一個 asn.1 物件識別元 (OID)。 OID 可識別用來計算雜湊的演算法。 您可以將演算法對應至物件識別碼, 以擴充密碼編譯機制以使用自訂演算法。 下列範例顯示如何將物件識別碼對應至新的雜湊演算法。  
  
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
  
 Y > 元素包含兩個屬性。 [ \< ](./file-schema/cryptography/oidentry-element.md) **OID**屬性是物件識別碼。 **Name**屬性是[ \<y > 元素](./file-schema/cryptography/nameentry-element.md)中**name**屬性的值。 在物件識別碼可以對應到簡單名稱之前, 必須先從演算法名稱對應至類別。  
  
## <a name="see-also"></a>另請參閱

- [設定密碼編譯類別](configure-cryptography-classes.md)
- [The signature is valid](../../standard/security/cryptographic-services.md)
