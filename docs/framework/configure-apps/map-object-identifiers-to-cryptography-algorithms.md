---
title: "對應物件識別項至密碼編譯演算法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: dbfe394193925e38dad774d39d79ac813abef22a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
