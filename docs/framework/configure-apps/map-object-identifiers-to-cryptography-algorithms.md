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
ms.openlocfilehash: d23fc48a53ee47aacfc290b52887b800ce37477f
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48263241"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="0c14e-102">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="0c14e-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="0c14e-103">數位簽章確認，資料未遭竄改時每個程式傳送到另一個。</span><span class="sxs-lookup"><span data-stu-id="0c14e-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="0c14e-104">通常透過將數學函式套用至要簽署之資料的雜湊計算數位簽章。</span><span class="sxs-lookup"><span data-stu-id="0c14e-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="0c14e-105">格式化時必須經過簽署的雜湊值，有些數位簽章演算法就會附加在格式化作業 ASN.1 物件識別碼 (OID)。</span><span class="sxs-lookup"><span data-stu-id="0c14e-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="0c14e-106">OID 識別用來計算雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="0c14e-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="0c14e-107">您可以將演算法對應至物件識別碼，若要擴充的密碼編譯機制，來使用自訂的演算法。</span><span class="sxs-lookup"><span data-stu-id="0c14e-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="0c14e-108">下列範例示範如何將物件識別項對應至新的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="0c14e-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="0c14e-109">[ \<OidEntry > 項目](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)包含兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="0c14e-109">The [\<oidEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="0c14e-110">**OID**屬性是物件識別碼數字。</span><span class="sxs-lookup"><span data-stu-id="0c14e-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="0c14e-111">**名稱**屬性是值**名稱**屬性從[ \<nameEntry > 項目](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)。</span><span class="sxs-lookup"><span data-stu-id="0c14e-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="0c14e-112">物件識別元可以對應至簡單名稱之前，必須是將演算法名稱對應至類別。</span><span class="sxs-lookup"><span data-stu-id="0c14e-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c14e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c14e-113">See Also</span></span>  
 [<span data-ttu-id="0c14e-114">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="0c14e-114">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="0c14e-115">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="0c14e-115">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
