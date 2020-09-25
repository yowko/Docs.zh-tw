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
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="3edaf-103">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="3edaf-103">Mapping Object Identifiers to Cryptography Algorithms</span></span>

<span data-ttu-id="3edaf-104">數位簽章可確保當資料從某個程式傳送到另一個程式時，不會遭到篡改。</span><span class="sxs-lookup"><span data-stu-id="3edaf-104">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="3edaf-105">通常，數位簽章的計算方式是將數學函數套用至要簽署的資料雜湊。</span><span class="sxs-lookup"><span data-stu-id="3edaf-105">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="3edaf-106">當您格式化要簽署的雜湊值時，某些數位簽章演算法會在格式化作業中附加 asn.1 物件識別碼 (OID) 。</span><span class="sxs-lookup"><span data-stu-id="3edaf-106">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="3edaf-107">OID 會識別用來計算雜湊的演算法。</span><span class="sxs-lookup"><span data-stu-id="3edaf-107">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="3edaf-108">您可以將演算法對應至物件識別碼，以擴充使用自訂演算法的密碼編譯機制。</span><span class="sxs-lookup"><span data-stu-id="3edaf-108">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="3edaf-109">下列範例顯示如何將物件識別碼對應至新的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="3edaf-109">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="3edaf-110">[ \<oidEntry> 元素](./file-schema/cryptography/oidentry-element.md)包含兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="3edaf-110">The [\<oidEntry> element](./file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="3edaf-111">**OID**屬性是物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="3edaf-111">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="3edaf-112">**Name**屬性是[ \<nameEntry> 元素](./file-schema/cryptography/nameentry-element.md)中**name**屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3edaf-112">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="3edaf-113">在物件識別碼可以對應至簡單名稱之前，必須先從演算法名稱對應至類別。</span><span class="sxs-lookup"><span data-stu-id="3edaf-113">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3edaf-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3edaf-114">See also</span></span>

- [<span data-ttu-id="3edaf-115">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="3edaf-115">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
- [<span data-ttu-id="3edaf-116">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="3edaf-116">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
