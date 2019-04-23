---
title: 向 COM 註冊組件
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 834652318d4cb1cbcebe27a922d210ef87026ed5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169022"
---
# <a name="registering-assemblies-with-com"></a><span data-ttu-id="9a982-102">向 COM 註冊組件</span><span class="sxs-lookup"><span data-stu-id="9a982-102">Registering Assemblies with COM</span></span>
<span data-ttu-id="9a982-103">您可以執行稱為[組件註冊工具 (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) 的命令列工具，註冊或取消登錄與 COM 搭配使用的組件。</span><span class="sxs-lookup"><span data-stu-id="9a982-103">You can run a command-line tool called the [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) to register or unregister an assembly for use with COM.</span></span> <span data-ttu-id="9a982-104">Regasm.exe 會將此類別的相關資訊新增至容器登錄，讓 COM 用戶端可以明確地使用 .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="9a982-104">Regasm.exe adds information about the class to the system registry so COM clients can use the .NET Framework class transparently.</span></span> <span data-ttu-id="9a982-105"><xref:System.Runtime.InteropServices.RegistrationServices> 類別提供對等功能。</span><span class="sxs-lookup"><span data-stu-id="9a982-105">The <xref:System.Runtime.InteropServices.RegistrationServices> class provides the equivalent functionality.</span></span>  
  
 <span data-ttu-id="9a982-106">必須先在 Windows 登錄中註冊 Managed 元件，才能從 COM 用戶端進行啟用。</span><span class="sxs-lookup"><span data-stu-id="9a982-106">A managed component must be registered in the Windows registry before it can be activated from a COM client.</span></span> <span data-ttu-id="9a982-107">下表顯示 Regasm.exe 通常會新增至 Windows 登錄的機碼</span><span class="sxs-lookup"><span data-stu-id="9a982-107">The following table shows the keys that Regasm.exe typically adds to the Windows registry.</span></span> <span data-ttu-id="9a982-108">(000000 表示實際 GUID 值)。</span><span class="sxs-lookup"><span data-stu-id="9a982-108">(000000 indicates the actual GUID value.)</span></span>  
  
|<span data-ttu-id="9a982-109">GUID</span><span class="sxs-lookup"><span data-stu-id="9a982-109">GUID</span></span>|<span data-ttu-id="9a982-110">說明</span><span class="sxs-lookup"><span data-stu-id="9a982-110">Description</span></span>|<span data-ttu-id="9a982-111">登錄機碼</span><span class="sxs-lookup"><span data-stu-id="9a982-111">Registry key</span></span>|  
|----------|-----------------|------------------|  
|<span data-ttu-id="9a982-112">CLSID</span><span class="sxs-lookup"><span data-stu-id="9a982-112">CLSID</span></span>|<span data-ttu-id="9a982-113">類別識別碼</span><span class="sxs-lookup"><span data-stu-id="9a982-113">Class identifier</span></span>|<span data-ttu-id="9a982-114">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="9a982-114">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span></span>|  
|<span data-ttu-id="9a982-115">IID</span><span class="sxs-lookup"><span data-stu-id="9a982-115">IID</span></span>|<span data-ttu-id="9a982-116">介面識別碼</span><span class="sxs-lookup"><span data-stu-id="9a982-116">Interface identifier</span></span>|<span data-ttu-id="9a982-117">HKEY_CLASSES_ROOT\Interface\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="9a982-117">HKEY_CLASSES_ROOT\Interface\\{000…000}</span></span>|  
|<span data-ttu-id="9a982-118">LIBID</span><span class="sxs-lookup"><span data-stu-id="9a982-118">LIBID</span></span>|<span data-ttu-id="9a982-119">程式庫識別碼</span><span class="sxs-lookup"><span data-stu-id="9a982-119">Library identifier</span></span>|<span data-ttu-id="9a982-120">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="9a982-120">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span></span>|  
|<span data-ttu-id="9a982-121">ProgID</span><span class="sxs-lookup"><span data-stu-id="9a982-121">ProgID</span></span>|<span data-ttu-id="9a982-122">程式設計識別碼</span><span class="sxs-lookup"><span data-stu-id="9a982-122">Programmatic identifier</span></span>|<span data-ttu-id="9a982-123">HKEY_CLASSES_ROOT\000…000</span><span class="sxs-lookup"><span data-stu-id="9a982-123">HKEY_CLASSES_ROOT\000…000</span></span>|  
  
 <span data-ttu-id="9a982-124">在 HKCR\CLSID\\{0000…0000} 機碼下，預設值設定為類別的 ProgID，並新增兩個新具名值：類別和組件。</span><span class="sxs-lookup"><span data-stu-id="9a982-124">Under the HKCR\CLSID\\{0000…0000} key, the default value is set to the ProgID of the class, and two new named values, Class and Assembly, are added.</span></span> <span data-ttu-id="9a982-125">執行階段會從登錄讀取 Assembly 值，並將它傳入執行階段組件解析程式。</span><span class="sxs-lookup"><span data-stu-id="9a982-125">The runtime reads the Assembly value from the registry and passes it on to the runtime assembly resolver.</span></span> <span data-ttu-id="9a982-126">組件解析程式會根據名稱和版本號碼這類組件資訊來嘗試找出組件。</span><span class="sxs-lookup"><span data-stu-id="9a982-126">The assembly resolver attempts to locate the assembly, based on assembly information such as the name and version number.</span></span> <span data-ttu-id="9a982-127">若要讓組件解析程式找到組件，組件必須位在下列其中一個位置：</span><span class="sxs-lookup"><span data-stu-id="9a982-127">For the assembly resolver to locate an assembly, the assembly has to be in one of the following locations:</span></span>  
  
-   <span data-ttu-id="9a982-128">全域組件快取 (必須是強式名稱組件)。</span><span class="sxs-lookup"><span data-stu-id="9a982-128">The global assembly cache (must be a strong-named assembly).</span></span>  
  
-   <span data-ttu-id="9a982-129">在應用程式目錄中。</span><span class="sxs-lookup"><span data-stu-id="9a982-129">In the application directory.</span></span> <span data-ttu-id="9a982-130">只有從該應用程式才能存取從應用程式路徑載入的組件。</span><span class="sxs-lookup"><span data-stu-id="9a982-130">Assemblies loaded from the application path are only accessible from that application.</span></span>  
  
-   <span data-ttu-id="9a982-131">使用 **/codebase** 選項所指定之 Regasm.exe 的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="9a982-131">Along an file path specified with the **/codebase** option to Regasm.exe.</span></span>  
  
 <span data-ttu-id="9a982-132">Regasm.exe 也會在 HKCR\CLSID\\{0000…0000} 機碼下建立 InProcServer32 機碼。</span><span class="sxs-lookup"><span data-stu-id="9a982-132">Regasm.exe also creates the InProcServer32 key under the HKCR\CLSID\\{0000…0000} key.</span></span> <span data-ttu-id="9a982-133">索引鍵的預設值設為初始化 Common Language Runtime 的 DLL 名稱 (Mscoree.dll)。</span><span class="sxs-lookup"><span data-stu-id="9a982-133">The default value for the key is set to the name of the DLL that initializes the common language runtime (Mscoree.dll).</span></span>  
  
## <a name="examining-registry-entries"></a><span data-ttu-id="9a982-134">檢查登錄項目</span><span class="sxs-lookup"><span data-stu-id="9a982-134">Examining Registry Entries</span></span>  
 <span data-ttu-id="9a982-135">COM Interop 提供標準 Class Factory 實作，來建立任何 .NET Framework 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9a982-135">COM interop provides a standard class factory implementation to create an instance of any .NET Framework class.</span></span> <span data-ttu-id="9a982-136">用戶端可以在 Managed DLL 上呼叫 **DllGetClassObject**，來取得 Class Factory 以及建立物件，就像使用任何其他 COM 元件一樣。</span><span class="sxs-lookup"><span data-stu-id="9a982-136">Clients can call **DllGetClassObject** on the managed DLL to get a class factory and create objects, just as they would with any other COM component.</span></span>  
  
 <span data-ttu-id="9a982-137">針對 `InprocServer32` 索引鍵，Mscoree.dll 的參考會取代傳統 COM 型別程式庫，以指出 Common Language Runtime 建立 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="9a982-137">For the `InprocServer32` subkey, a reference to Mscoree.dll appears in place of a traditional COM type library to indicate that the common language runtime creates the managed object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a982-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a982-138">See also</span></span>

- [<span data-ttu-id="9a982-139">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="9a982-139">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="9a982-140">作法：參考 COM 的 .NET 類型</span><span class="sxs-lookup"><span data-stu-id="9a982-140">How to: Reference .NET Types from COM</span></span>](how-to-reference-net-types-from-com.md)
- [<span data-ttu-id="9a982-141">呼叫 .NET 物件</span><span class="sxs-lookup"><span data-stu-id="9a982-141">Calling a .NET Object</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [<span data-ttu-id="9a982-142">部署供 COM 存取的應用程式</span><span class="sxs-lookup"><span data-stu-id="9a982-142">Deploying an Application for COM Access</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
