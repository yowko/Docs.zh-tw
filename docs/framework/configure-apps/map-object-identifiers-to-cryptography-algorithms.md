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
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="35651-102">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="35651-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="35651-103">數位簽章可確保資料從某個程式傳送至另一個程式時, 不會遭到篡改。</span><span class="sxs-lookup"><span data-stu-id="35651-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="35651-104">通常數位簽章的計算方式是將數學函式套用到要簽署的資料雜湊。</span><span class="sxs-lookup"><span data-stu-id="35651-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="35651-105">格式化要簽署的雜湊值時, 某些數位簽章演算法會在格式化作業中附加一個 asn.1 物件識別元 (OID)。</span><span class="sxs-lookup"><span data-stu-id="35651-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="35651-106">OID 可識別用來計算雜湊的演算法。</span><span class="sxs-lookup"><span data-stu-id="35651-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="35651-107">您可以將演算法對應至物件識別碼, 以擴充密碼編譯機制以使用自訂演算法。</span><span class="sxs-lookup"><span data-stu-id="35651-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="35651-108">下列範例顯示如何將物件識別碼對應至新的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="35651-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="35651-109">Y > 元素包含兩個屬性。 [ \< ](./file-schema/cryptography/oidentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="35651-109">The [\<oidEntry> element](./file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="35651-110">**OID**屬性是物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="35651-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="35651-111">**Name**屬性是[ \<y > 元素](./file-schema/cryptography/nameentry-element.md)中**name**屬性的值。</span><span class="sxs-lookup"><span data-stu-id="35651-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="35651-112">在物件識別碼可以對應到簡單名稱之前, 必須先從演算法名稱對應至類別。</span><span class="sxs-lookup"><span data-stu-id="35651-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35651-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35651-113">See also</span></span>

- [<span data-ttu-id="35651-114">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="35651-114">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
- [<span data-ttu-id="35651-115">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="35651-115">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
