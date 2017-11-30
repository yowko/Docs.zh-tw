---
title: "將演算法名稱對應至密碼編譯類別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e59b2551545b8b70bcb54a5d43d041c44579b786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="27677-102">將演算法名稱對應至密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="27677-102">Mapping Algorithm Names to Cryptography Classes</span></span>
<span data-ttu-id="27677-103">有四種方式，開發人員可以建立密碼編譯物件，使用[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="27677-103">There are four ways a developer can create a cryptography object using the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:</span></span>  
  
-   <span data-ttu-id="27677-104">建立物件，使用**新**運算子。</span><span class="sxs-lookup"><span data-stu-id="27677-104">Create an object by using the **new** operator.</span></span>  
  
-   <span data-ttu-id="27677-105">建立可實作特定密碼編譯演算法藉由呼叫物件**建立**該演算法的抽象類別上的方法。</span><span class="sxs-lookup"><span data-stu-id="27677-105">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
-   <span data-ttu-id="27677-106">建立可實作特定密碼編譯演算法藉由呼叫物件<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="27677-106">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="27677-107">建立該物件會實作密碼編譯演算法 （例如對稱的區塊編碼器） 的類別，藉由呼叫**建立**抽象類別上的方法為該類型的演算法 (例如<xref:System.Security.Cryptography.SymmetricAlgorithm>)。</span><span class="sxs-lookup"><span data-stu-id="27677-107">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="27677-108">例如，假設開發人員想要計算的一組位元組的 SHA1 雜湊。</span><span class="sxs-lookup"><span data-stu-id="27677-108">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="27677-109"><xref:System.Security.Cryptography>命名空間包含兩個的 SHA1 演算法，一個純粹是 managed 的實作，另一個包裝 CryptoAPI 實作。</span><span class="sxs-lookup"><span data-stu-id="27677-109">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="27677-110">開發人員可以選擇來具現化特定的 SHA1 實作 (例如<xref:System.Security.Cryptography.SHA1Managed>) 藉由呼叫**新**運算子。</span><span class="sxs-lookup"><span data-stu-id="27677-110">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="27677-111">不過，如果它並不重要，只要在類別實作的 SHA1 雜湊演算法，common language runtime 載入哪一個類別，開發人員可以建立物件藉由呼叫<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="27677-111">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="27677-112">這個方法會呼叫**System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**，它必須傳回 SHA1 雜湊演算法的實作。</span><span class="sxs-lookup"><span data-stu-id="27677-112">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="27677-113">開發人員也可以呼叫**System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")**因為依預設，加密組態包含隨附於.NET Framework 中的演算法的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="27677-113">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="27677-114">如果不論使用哪一個雜湊演算法，開發人員可以呼叫<xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType>方法，傳回實作雜湊轉換的物件。</span><span class="sxs-lookup"><span data-stu-id="27677-114">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="27677-115">將組態檔中的演算法名稱對應</span><span class="sxs-lookup"><span data-stu-id="27677-115">Mapping Algorithm Names in Configuration Files</span></span>  
 <span data-ttu-id="27677-116">根據預設，執行階段傳回<xref:System.Security.Cryptography.SHA1CryptoServiceProvider>所有四個案例中的物件。</span><span class="sxs-lookup"><span data-stu-id="27677-116">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="27677-117">不過，電腦的系統管理員可以變更最後兩個案例中的方法傳回的物件的類型。</span><span class="sxs-lookup"><span data-stu-id="27677-117">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="27677-118">若要這樣做，您必須將易記的演算法名稱對應至您想要使用電腦組態檔 (Machine.config) 中的類別。</span><span class="sxs-lookup"><span data-stu-id="27677-118">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="27677-119">下列範例示範如何設定執行階段，讓**System.Security.Cryptography.SHA1.Create**， **System.Security.CryptoConfig.CreateFromName("SHA1")**，和**System.Security.Cryptography.HashAlgorithm.Create**傳回`MySHA1HashClass`物件。</span><span class="sxs-lookup"><span data-stu-id="27677-119">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="27677-120">您可以指定在屬性名稱的[< cryptoClass\>元素](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)(上一個範例將此屬性命名`MySHA1Hash`)。</span><span class="sxs-lookup"><span data-stu-id="27677-120">You can specify the name of the attribute in the [<cryptoClass\> element](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="27677-121">中的屬性值 **\<cryptoClass >**元素是 common language runtime 用來尋找類別的字串。</span><span class="sxs-lookup"><span data-stu-id="27677-121">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="27677-122">您可以使用符合在指定之需求的任何字串[指定限定的型別名稱](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="27677-122">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="27677-123">許多的演算法名稱可以對應至相同的類別。</span><span class="sxs-lookup"><span data-stu-id="27677-123">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="27677-124">[ \<y > 項目](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)類別對應至一個易記的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="27677-124">The [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="27677-125">**名稱**屬性可以是任一個字串時，呼叫使用**System.Security.Cryptography.CryptoConfig.CreateFromName**方法或在抽象的密碼編譯類別的名稱<xref:System.Security.Cryptography>命名空間。</span><span class="sxs-lookup"><span data-stu-id="27677-125">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="27677-126">值**類別**屬性是中的屬性名稱 **\<cryptoClass >**項目。</span><span class="sxs-lookup"><span data-stu-id="27677-126">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27677-127">您可以藉由呼叫取得 SHA1 演算法<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>或**Security.CryptoConfig.CreateFromName("SHA1")**方法。</span><span class="sxs-lookup"><span data-stu-id="27677-127">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="27677-128">每個方法僅保證，它會傳回實作 SHA1 演算法的物件。</span><span class="sxs-lookup"><span data-stu-id="27677-128">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="27677-129">沒有對應至相同的類別，在組態檔中的每個演算法的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="27677-129">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="27677-130">如需預設名稱和它們對應到類別的清單，請參閱<xref:System.Security.Cryptography.CryptoConfig>。</span><span class="sxs-lookup"><span data-stu-id="27677-130">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27677-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27677-131">See Also</span></span>  
 [<span data-ttu-id="27677-132">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="27677-132">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="27677-133">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="27677-133">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
