---
title: 將演算法名稱對應至密碼編譯類別
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 513000169504473aa6dd46feaca214f58502ffd0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912872"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="ef7eb-102">將演算法名稱對應至密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="ef7eb-102">Mapping Algorithm Names to Cryptography Classes</span></span>
<span data-ttu-id="ef7eb-103">有四種方式可供開發人員使用 Windows SDK 建立密碼編譯物件:</span><span class="sxs-lookup"><span data-stu-id="ef7eb-103">There are four ways a developer can create a cryptography object using the Windows SDK:</span></span>  
  
- <span data-ttu-id="ef7eb-104">使用**new**運算子建立物件。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-104">Create an object by using the **new** operator.</span></span>  
  
- <span data-ttu-id="ef7eb-105">在該演算法的抽象類別上呼叫**create**方法, 以建立可執行特定密碼編譯演算法的物件。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-105">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
- <span data-ttu-id="ef7eb-106">藉由呼叫<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法, 建立可執行特定密碼編譯演算法的物件。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-106">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="ef7eb-107">藉由在該演算法類型的抽象類別 (例如<xref:System.Security.Cryptography.SymmetricAlgorithm>) 上呼叫**create**方法, 來建立可實作為密碼編譯演算法類別 (例如對稱式封鎖密碼) 的物件。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-107">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="ef7eb-108">例如, 假設開發人員想要計算一組位元組的 SHA1 雜湊。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-108">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="ef7eb-109"><xref:System.Security.Cryptography>命名空間包含兩種 SHA1 演算法的實作為, 一個純粹受控的執行, 另一個則包裝 CryptoAPI。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-109">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="ef7eb-110">開發人員可以藉由呼叫**new**運算子, 選擇具現化特定<xref:System.Security.Cryptography.SHA1Managed>的 SHA1 實作為 (例如)。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-110">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="ef7eb-111">不過, 如果通用語言執行平臺在類別實作為 SHA1 雜湊演算法時所載入的類別並不重要, 則開發人員可以藉由呼叫<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>方法來建立物件。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-111">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ef7eb-112">這個方法會呼叫**cryptoconfig.createfromname. CreateFromName ("system.string")** , 它必須傳回 SHA1 雜湊演算法的實值。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-112">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="ef7eb-113">開發人員也可以呼叫**cryptoconfig.createfromname. CreateFromName ("SHA1")** , 因為根據預設, 密碼編譯設定會包含 .NET Framework 隨附之演算法的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-113">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="ef7eb-114">如果使用的雜湊演算法並不重要, 開發人員可以呼叫<xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType>方法, 它會傳回可執行雜湊轉換的物件。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-114">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="ef7eb-115">對應設定檔中的演算法名稱</span><span class="sxs-lookup"><span data-stu-id="ef7eb-115">Mapping Algorithm Names in Configuration Files</span></span>  
 <span data-ttu-id="ef7eb-116">根據預設, 運行<xref:System.Security.Cryptography.SHA1CryptoServiceProvider>時間會針對所有四個案例傳回物件。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-116">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="ef7eb-117">不過, 電腦系統管理員可以變更最後兩個案例中的方法所傳回的物件類型。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-117">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="ef7eb-118">若要這樣做, 您必須將易記的演算法名稱對應至您想要在電腦設定檔案 (Machine.config) 中使用的類別。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-118">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="ef7eb-119">下列範例會示範如何設定執行時間, 使**Cryptoconfig.createfromname CreateFromName ("SHA1")** , 以及 **HashAlgorithm. 建立程式中的執行密碼編譯。 create。傳回物件。** `MySHA1HashClass`</span><span class="sxs-lookup"><span data-stu-id="ef7eb-119">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
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
  
 <span data-ttu-id="ef7eb-120">您可以在[< cryptoClass\> ](./file-schema/cryptography/cryptoclass-element.md)專案中指定屬性的名稱 (先前的範例會將屬性`MySHA1Hash`命名為)。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-120">You can specify the name of the attribute in the [<cryptoClass\> element](./file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="ef7eb-121">CryptoClass > 元素中 **\<** 的屬性值是通用語言執行時間用來尋找類別的字串。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-121">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="ef7eb-122">您可以使用符合指定[完整類型名稱](../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的任何字串。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-122">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="ef7eb-123">許多演算法名稱可以對應至相同的類別。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-123">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="ef7eb-124">Y > 元素會將類別對應至一個易記的演算法名稱。 [ \< ](./file-schema/cryptography/nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="ef7eb-124">The [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="ef7eb-125">**Name**屬性可以是在<xref:System.Security.Cryptography>命名空間中呼叫**cryptoconfig.createfromname. CreateFromName**方法或抽象密碼編譯類別名稱時所使用的字串。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-125">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="ef7eb-126">**類別**屬性的值是 **\<cryptoClass >** 元素中的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-126">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef7eb-127">您可以藉由呼叫<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>或**cryptoconfig.createfromname. CreateFromName ("SHA1")** 方法來取得 SHA1 演算法。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-127">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="ef7eb-128">每個方法都只保證它會傳回可實作為 SHA1 演算法的物件。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-128">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="ef7eb-129">您不需要將演算法的每一個易記名稱對應至設定檔中的相同類別。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-129">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="ef7eb-130">如需預設名稱及其對應類別的清單, 請參閱<xref:System.Security.Cryptography.CryptoConfig>。</span><span class="sxs-lookup"><span data-stu-id="ef7eb-130">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef7eb-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef7eb-131">See also</span></span>

- [<span data-ttu-id="ef7eb-132">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="ef7eb-132">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ef7eb-133">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="ef7eb-133">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
