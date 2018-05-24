---
title: 如何：使用 Tlbimp.exe 產生主要 Interop 組件
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74c196c0f6525214e2ea25e6506e9c89f4e48906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="74f68-102">如何：使用 Tlbimp.exe 產生主要 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="74f68-102">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>
<span data-ttu-id="74f68-103">有兩種方式可產生主要 Interop 組件：</span><span class="sxs-lookup"><span data-stu-id="74f68-103">There are two ways to generate a primary interop assembly:</span></span>  
  
-   <span data-ttu-id="74f68-104">使用 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 提供的[型別程式庫匯入工具 (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)。</span><span class="sxs-lookup"><span data-stu-id="74f68-104">Using the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
     <span data-ttu-id="74f68-105">產生主要 Interop 組件最直接的方法是使用[型別程式庫匯入工具 (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)。</span><span class="sxs-lookup"><span data-stu-id="74f68-105">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="74f68-106">Tlbimp.exe 會提供下列保護措施：</span><span class="sxs-lookup"><span data-stu-id="74f68-106">Tlbimp.exe provides the following safeguards:</span></span>  
  
    -   <span data-ttu-id="74f68-107">建立任何巢狀類型程式庫參考的新 Interop 組件之前，檢查是否有其他已註冊的主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="74f68-107">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>  
  
    -   <span data-ttu-id="74f68-108">如果您未指定容器或檔案名稱，來指定主要 Interop 組件的強式名稱，則無法發出主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="74f68-108">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>  
  
    -   <span data-ttu-id="74f68-109">如果您省略相依組件的參考，則無法發出主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="74f68-109">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>  
  
    -   <span data-ttu-id="74f68-110">如果您加入非主要 Interop 組件的相依組件的參考，則無法發出主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="74f68-110">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>  
  
-   <span data-ttu-id="74f68-111">使用與 Common Language Specification (CLS) 相容的語言，例如 C#，在原始程式碼中手動建立主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="74f68-111">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="74f68-112">無法使用類型程式庫時，這個方法就很有用。</span><span class="sxs-lookup"><span data-stu-id="74f68-112">This approach is useful when a type library is unavailable.</span></span>  
  
 <span data-ttu-id="74f68-113">您必須使用密碼編譯金鑰組將組件簽署為強式名稱。</span><span class="sxs-lookup"><span data-stu-id="74f68-113">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="74f68-114">如需詳細資料，請參閱[建立金鑰組](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)。</span><span class="sxs-lookup"><span data-stu-id="74f68-114">For details, see [Creating A Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="74f68-115">使用 Tlbimp.exe 產生主要 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="74f68-115">To generate a primary interop assembly using Tlbimp.exe</span></span>  
  
1.  <span data-ttu-id="74f68-116">在命令提示中，輸入：</span><span class="sxs-lookup"><span data-stu-id="74f68-116">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="74f68-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span><span class="sxs-lookup"><span data-stu-id="74f68-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>  
  
     <span data-ttu-id="74f68-118">在這個命令中，*tlbfile* 是含有 COM 類型程式庫的檔案，*filename* 是含有金鑰組的容器或檔案名稱，而 *assemblyname* 則是要簽署為強式名稱的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="74f68-118">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>  
  
 <span data-ttu-id="74f68-119">主要 Interop 組件只能參考其他主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="74f68-119">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="74f68-120">如果您的組件參考來自協力廠商 COM 類型程式庫的類型，則您必須先從發行者取得主要 Interop 組件，才能產生主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="74f68-120">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="74f68-121">如果您是發行者，您必須先產生相依類別程式庫的主要 Interop 組件，才能產生參考的主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="74f68-121">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>  
  
 <span data-ttu-id="74f68-122">安裝在目前的目錄時，無法探索與原始類型程式庫版本號碼不同的相依主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="74f68-122">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="74f68-123">您必須在 Windows 登錄中登錄相依的主要 Interop 組件，或使用 **/reference** 選項，以確定 Tlbimp.exe 能找到相依的 DLL。</span><span class="sxs-lookup"><span data-stu-id="74f68-123">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>  
  
 <span data-ttu-id="74f68-124">您也可以包裝類型程式庫的多個版本。</span><span class="sxs-lookup"><span data-stu-id="74f68-124">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="74f68-125">如需相關指示，請參閱[如何：包裝型別程式庫的多個版本](https://msdn.microsoft.com/library/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="74f68-125">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](https://msdn.microsoft.com/library/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="74f68-126">範例</span><span class="sxs-lookup"><span data-stu-id="74f68-126">Example</span></span>  
 <span data-ttu-id="74f68-127">下列範例會匯入 COM 類型程式庫  `LibUtil.tlb`，並使用金鑰檔案 `CompanyA.snk` 將組件 `LibUtil.dll` 簽署為強式名稱。</span><span class="sxs-lookup"><span data-stu-id="74f68-127">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="74f68-128">藉由略過特定命名空間名稱，此範例會產生預設的命名空間 `LibUtil`。</span><span class="sxs-lookup"><span data-stu-id="74f68-128">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 <span data-ttu-id="74f68-129">如需更具描述性的名稱 (使用 *VendorName*.*LibraryName* 命名指導方針)，下列範例會覆寫預設組件檔案名稱和命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="74f68-129">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 <span data-ttu-id="74f68-130">下列範例會匯入 `MyLib.tlb`，它參考 `CompanyA.LibUtil.dll` 並使用金鑰檔案 `CompanyB.snk` 將組件 `CompanyB.MyLib.dll` 簽署為強式名稱。</span><span class="sxs-lookup"><span data-stu-id="74f68-130">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="74f68-131">命名空間 `CompanyB.MyLib` 會覆寫預設命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="74f68-131">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="74f68-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="74f68-132">See Also</span></span>  
 [<span data-ttu-id="74f68-133">如何：登錄主要 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="74f68-133">How to: Register Primary Interop Assemblies</span></span>](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
