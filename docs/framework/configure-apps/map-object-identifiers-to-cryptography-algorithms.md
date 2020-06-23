---
title: 對應物件識別項至密碼編譯演算法
description: 請參閱如何使用 XML 設定檔中的 y 和 y 元素，將物件識別碼（OID）對應至 .NET 中的密碼編譯演算法。
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: e22510014071455b83ba28cd82690b5ecdce9bc9
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2020
ms.locfileid: "85142000"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>對應物件識別項至密碼編譯演算法
數位簽章可確保資料從某個程式傳送至另一個程式時，不會遭到篡改。 通常數位簽章的計算方式是將數學函式套用到要簽署的資料雜湊。 格式化要簽署的雜湊值時，某些數位簽章演算法會在格式化作業中附加一個 asn.1 物件識別元（OID）。 OID 可識別用來計算雜湊的演算法。 您可以將演算法對應至物件識別碼，以擴充密碼編譯機制以使用自訂演算法。 下列範例顯示如何將物件識別碼對應至新的雜湊演算法。  
  
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
  
 [ \<oidEntry> 元素](./file-schema/cryptography/oidentry-element.md)包含兩個屬性。 **OID**屬性是物件識別碼。 **Name**屬性是來自[ \<nameEntry> 元素](./file-schema/cryptography/nameentry-element.md)的**name**屬性值。 在物件識別碼可以對應到簡單名稱之前，必須先從演算法名稱對應至類別。  
  
## <a name="see-also"></a>另請參閱

- [設定密碼編譯類別](configure-cryptography-classes.md)
- [密碼編譯服務](../../standard/security/cryptographic-services.md)
