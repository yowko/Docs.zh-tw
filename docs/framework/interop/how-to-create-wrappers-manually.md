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
# <a name="how-to-create-wrappers-manually"></a>作法：手動建立包裝函式
若您決定在 Managed 原始程式碼中手動宣告 COM 類型，現有的介面定義語言 (IDL) 檔或類型程式庫，將會是最佳的啟動位置。 沒有 IDL 檔案或無法產生類型程式庫檔案時，可建立 Managed 宣告並將所產生的組件匯出至類型程式庫，進而模擬 COM類型。  
  
### <a name="to-simulate-com-types-from-managed-source"></a>從 Managed 原始檔模擬 COM 類型  
  
1. 在與 Common Language Specification (CLS) 相容的語言中宣告類型，並編譯其檔案。  
  
2. 匯出含有[型別程式庫匯出工具 (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) 類型的組件。  
  
3. 使用匯出的 COM 類型程式庫做為基礎，來宣告以 COM 為中心的 Managed 類型。  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a>若要建立執行階段可呼叫包裝函式 (RCW)  
  
1. 假設您有一個 IDL 檔案或類型程式庫檔案，請決定要將哪些類別及介面納入自訂 RCW 中。 您可以在應用程式中直接或間接地排除任何不會使用的類型。  
  
2. 在符合 CLS 標準的語言中建立原始程式檔，並宣告其類型。 請參閱[型別程式庫至組件轉換的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) ，以取得匯入轉換程序的完整描述。 建立自訂 RCW 時，您實際上是手動執行[型別程式庫匯入工具 (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) 所提供的類型轉換活動。 下一節的範例將示範 IDL 或類型程式庫檔案中的類型，以及這些類型在 C# 程式碼中對應的類型。  
  
3. 宣告完成時，即可使用編譯任何其他 Managed 原始程式碼的方式來編譯檔案。  
  
4. 如同使用 Tlbimp.exe 匯入類型一樣，部分檔案會要求額外的資訊，其可由您直接加入程式碼。 如需詳細資訊，請參閱[如何：編輯 Interop 組件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))。  
  
## <a name="example"></a>範例  
 下列程式碼為 `ISATest` 介面，和 IDL 中 `SATest` 類別以及C# 原始程式碼中對應類型的範例。  
  
 **IDL 或型別程式庫檔案**  
  
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
  
 **受控原始程式碼中的包裝函式**  
  
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
  
## <a name="see-also"></a>另請參閱

- [自訂執行階段可呼叫包裝函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))
- [COM 資料類型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))
- [作法：編輯 Interop 組件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))
- [型別程式庫至組件轉換的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tlbimp.exe (類型程式庫匯入工具)](../tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (類型程式庫匯出工具)](../tools/tlbexp-exe-type-library-exporter.md)
