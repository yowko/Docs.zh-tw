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
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="1ab8f-102">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="1ab8f-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="1ab8f-103">數位簽章確認，資料未遭竄改時每個程式傳送到另一個。</span><span class="sxs-lookup"><span data-stu-id="1ab8f-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="1ab8f-104">通常就是透過將數學函式套用至要簽署資料的雜湊計算數位簽章。</span><span class="sxs-lookup"><span data-stu-id="1ab8f-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="1ab8f-105">格式化時要簽署的雜湊值，有些數位簽章演算法就會附加在格式化作業的一部分 ASN.1 物件識別碼 (OID)。</span><span class="sxs-lookup"><span data-stu-id="1ab8f-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="1ab8f-106">OID 識別用來計算雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="1ab8f-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="1ab8f-107">您可以將演算法對應至物件識別碼，來擴充要使用的自訂演算法的新一代密碼編譯機制。</span><span class="sxs-lookup"><span data-stu-id="1ab8f-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="1ab8f-108">下列範例會示範如何將物件識別碼對應至新的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="1ab8f-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="1ab8f-109">[ \<OidEntry > 項目](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)包含兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="1ab8f-109">The [\<oidEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="1ab8f-110">**OID**屬性是物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="1ab8f-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="1ab8f-111">**名稱**屬性是值**名稱**屬性從[ \<y > 項目](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)。</span><span class="sxs-lookup"><span data-stu-id="1ab8f-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="1ab8f-112">物件識別元可以對應至簡單名稱之前，必須是從演算法名稱對應至類別。</span><span class="sxs-lookup"><span data-stu-id="1ab8f-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ab8f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ab8f-113">See Also</span></span>  
 [<span data-ttu-id="1ab8f-114">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="1ab8f-114">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="1ab8f-115">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="1ab8f-115">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
