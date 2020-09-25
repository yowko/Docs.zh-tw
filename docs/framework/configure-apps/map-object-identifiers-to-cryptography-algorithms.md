---
title: 對應物件識別項至密碼編譯演算法
description: 瞭解如何使用 XML 設定檔中的 y 和 y 專案，將物件識別碼 (OID) 對應至 .NET 中的密碼編譯演算法。
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: 5416ddbb766dfde56fa28a3853ed448cc73f25a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189379"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>對應物件識別項至密碼編譯演算法

數位簽章可確保當資料從某個程式傳送到另一個程式時，不會遭到篡改。 通常，數位簽章的計算方式是將數學函數套用至要簽署的資料雜湊。 當您格式化要簽署的雜湊值時，某些數位簽章演算法會在格式化作業中附加 asn.1 物件識別碼 (OID) 。 OID 會識別用來計算雜湊的演算法。 您可以將演算法對應至物件識別碼，以擴充使用自訂演算法的密碼編譯機制。 下列範例顯示如何將物件識別碼對應至新的雜湊演算法。  
  
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
  
 [ \<oidEntry> 元素](./file-schema/cryptography/oidentry-element.md)包含兩個屬性。 **OID**屬性是物件識別碼。 **Name**屬性是[ \<nameEntry> 元素](./file-schema/cryptography/nameentry-element.md)中**name**屬性的值。 在物件識別碼可以對應至簡單名稱之前，必須先從演算法名稱對應至類別。  
  
## <a name="see-also"></a>另請參閱

- [設定密碼編譯類別](configure-cryptography-classes.md)
- [密碼編譯服務](../../standard/security/cryptographic-services.md)
