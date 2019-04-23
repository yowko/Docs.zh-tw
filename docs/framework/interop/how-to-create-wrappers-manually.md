---
title: 作法：手動建立包裝函式
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f834eb52476e9b04ed6aaf294deed88213961045
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304242"
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="283c6-102">作法：手動建立包裝函式</span><span class="sxs-lookup"><span data-stu-id="283c6-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="283c6-103">若您決定在 Managed 原始程式碼中手動宣告 COM 類型，現有的介面定義語言 (IDL) 檔或類型程式庫，將會是最佳的啟動位置。</span><span class="sxs-lookup"><span data-stu-id="283c6-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="283c6-104">沒有 IDL 檔案或無法產生類型程式庫檔案時，可建立 Managed 宣告並將所產生的組件匯出至類型程式庫，進而模擬 COM類型。</span><span class="sxs-lookup"><span data-stu-id="283c6-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="283c6-105">從 Managed 原始檔模擬 COM 類型</span><span class="sxs-lookup"><span data-stu-id="283c6-105">To simulate COM types from managed source</span></span>  
  
1. <span data-ttu-id="283c6-106">在與 Common Language Specification (CLS) 相容的語言中宣告類型，並編譯其檔案。</span><span class="sxs-lookup"><span data-stu-id="283c6-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2. <span data-ttu-id="283c6-107">匯出含有[型別程式庫匯出工具 (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) 類型的組件。</span><span class="sxs-lookup"><span data-stu-id="283c6-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3. <span data-ttu-id="283c6-108">使用匯出的 COM 類型程式庫做為基礎，來宣告以 COM 為中心的 Managed 類型。</span><span class="sxs-lookup"><span data-stu-id="283c6-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="283c6-109">若要建立執行階段可呼叫包裝函式 (RCW)</span><span class="sxs-lookup"><span data-stu-id="283c6-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1. <span data-ttu-id="283c6-110">假設您有一個 IDL 檔案或類型程式庫檔案，請決定要將哪些類別及介面納入自訂 RCW 中。</span><span class="sxs-lookup"><span data-stu-id="283c6-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="283c6-111">您可以在應用程式中直接或間接地排除任何不會使用的類型。</span><span class="sxs-lookup"><span data-stu-id="283c6-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2. <span data-ttu-id="283c6-112">在符合 CLS 標準的語言中建立原始程式檔，並宣告其類型。</span><span class="sxs-lookup"><span data-stu-id="283c6-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="283c6-113">請參閱[型別程式庫至組件轉換的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) ，以取得匯入轉換程序的完整描述。</span><span class="sxs-lookup"><span data-stu-id="283c6-113">See [Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) for a complete description of the import conversion process.</span></span> <span data-ttu-id="283c6-114">建立自訂 RCW 時，您實際上是手動執行[型別程式庫匯入工具 (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) 所提供的類型轉換活動。</span><span class="sxs-lookup"><span data-stu-id="283c6-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="283c6-115">下一節的範例將示範 IDL 或類型程式庫檔案中的類型，以及這些類型在 C# 程式碼中對應的類型。</span><span class="sxs-lookup"><span data-stu-id="283c6-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3. <span data-ttu-id="283c6-116">宣告完成時，即可使用編譯任何其他 Managed 原始程式碼的方式來編譯檔案。</span><span class="sxs-lookup"><span data-stu-id="283c6-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4. <span data-ttu-id="283c6-117">如同使用 Tlbimp.exe 匯入類型一樣，部分檔案會要求額外的資訊，其可由您直接加入程式碼。</span><span class="sxs-lookup"><span data-stu-id="283c6-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="283c6-118">如需詳細資訊，請參閱[如何：編輯 Interop 組件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="283c6-118">For details, see [How to: Edit Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="283c6-119">範例</span><span class="sxs-lookup"><span data-stu-id="283c6-119">Example</span></span>  
 <span data-ttu-id="283c6-120">下列程式碼為 `ISATest` 介面，和 IDL 中 `SATest` 類別以及C# 原始程式碼中對應類型的範例。</span><span class="sxs-lookup"><span data-stu-id="283c6-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 **<span data-ttu-id="283c6-121">IDL 或型別程式庫檔案</span><span class="sxs-lookup"><span data-stu-id="283c6-121">IDL or type library file</span></span>**  
  
```  
 [  
object,  
uuid(40A8C65D-2448-447A-B786-64682CBEF133),  
dual,  
helpstring("ISATest Interface"),  
pointer_default(unique)  
 ]  
interface ISATest : IDispatch  
 {  
[id(1), helpstring("method InSArray")]   
HRESULT InSArray([in] SAFEARRAY(int) *ppsa, [out,retval] int *pSum);  
 };  
 [  
uuid(116CCA1E-7E39-4515-9849-90790DA6431E),  
helpstring("SATest Class")  
 ]  
coclass SATest  
 {  
  [default] interface ISATest;  
 };  
```  
  
 **<span data-ttu-id="283c6-122">受控原始程式碼中的包裝函式</span><span class="sxs-lookup"><span data-stu-id="283c6-122">Wrapper in managed source code</span></span>**  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
using System.Runtime.CompilerServices;  
  
[assembly:Guid("E4A992B8-6F5C-442C-96E7-C4778924C753")]  
[assembly:ImportedFromTypeLib("SAServerLib")]  
namespace SAServer  
{  
 [ComImport]  
 [Guid("40A8C65D-2448-447A-B786-64682CBEF133")]  
 [TypeLibType(TypeLibTypeFlags.FLicensed)]  
 public interface ISATest  
 {  
  [DispId(1)]  
  //[MethodImpl(MethodImplOptions.InternalCall,  
  // MethodCodeType=MethodCodeType.Runtime)]  
  int InSArray( [MarshalAs(UnmanagedType.SafeArray,  
      SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }   
 [ComImport]  
 [Guid("116CCA1E-7E39-4515-9849-90790DA6431E")]  
 [ClassInterface(ClassInterfaceType.None)]  
 [TypeLibType(TypeLibTypeFlags.FCanCreate)]  
 public class SATest : ISATest  
 {  
  [DispId(1)]  
  [MethodImpl(MethodImplOptions.InternalCall,   
  MethodCodeType=MethodCodeType.Runtime)]  
  extern int ISATest.InSArray( [MarshalAs(UnmanagedType.SafeArray,   
  SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="283c6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="283c6-123">See also</span></span>

- [<span data-ttu-id="283c6-124">自訂執行階段可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="283c6-124">Customizing Runtime Callable Wrappers</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))
- [<span data-ttu-id="283c6-125">COM 資料類型</span><span class="sxs-lookup"><span data-stu-id="283c6-125">COM Data Types</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))
- [<span data-ttu-id="283c6-126">作法：編輯 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="283c6-126">How to: Edit Interop Assemblies</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))
- [<span data-ttu-id="283c6-127">型別程式庫至組件轉換的摘要</span><span class="sxs-lookup"><span data-stu-id="283c6-127">Type Library to Assembly Conversion Summary</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [<span data-ttu-id="283c6-128">Tlbimp.exe (類型程式庫匯入工具)</span><span class="sxs-lookup"><span data-stu-id="283c6-128">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="283c6-129">Tlbexp.exe (類型程式庫匯出工具)</span><span class="sxs-lookup"><span data-stu-id="283c6-129">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
