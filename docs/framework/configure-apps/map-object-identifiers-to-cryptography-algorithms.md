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
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="1e266-103">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="1e266-103">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="1e266-104">數位簽章可確保資料從某個程式傳送至另一個程式時，不會遭到篡改。</span><span class="sxs-lookup"><span data-stu-id="1e266-104">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="1e266-105">通常數位簽章的計算方式是將數學函式套用到要簽署的資料雜湊。</span><span class="sxs-lookup"><span data-stu-id="1e266-105">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="1e266-106">格式化要簽署的雜湊值時，某些數位簽章演算法會在格式化作業中附加一個 asn.1 物件識別元（OID）。</span><span class="sxs-lookup"><span data-stu-id="1e266-106">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="1e266-107">OID 可識別用來計算雜湊的演算法。</span><span class="sxs-lookup"><span data-stu-id="1e266-107">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="1e266-108">您可以將演算法對應至物件識別碼，以擴充密碼編譯機制以使用自訂演算法。</span><span class="sxs-lookup"><span data-stu-id="1e266-108">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="1e266-109">下列範例顯示如何將物件識別碼對應至新的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="1e266-109">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="1e266-110">[ \<oidEntry> 元素](./file-schema/cryptography/oidentry-element.md)包含兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="1e266-110">The [\<oidEntry> element](./file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="1e266-111">**OID**屬性是物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="1e266-111">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="1e266-112">**Name**屬性是來自[ \<nameEntry> 元素](./file-schema/cryptography/nameentry-element.md)的**name**屬性值。</span><span class="sxs-lookup"><span data-stu-id="1e266-112">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="1e266-113">在物件識別碼可以對應到簡單名稱之前，必須先從演算法名稱對應至類別。</span><span class="sxs-lookup"><span data-stu-id="1e266-113">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e266-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e266-114">See also</span></span>

- [<span data-ttu-id="1e266-115">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="1e266-115">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
- [<span data-ttu-id="1e266-116">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="1e266-116">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
