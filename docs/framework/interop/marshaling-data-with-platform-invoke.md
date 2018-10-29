---
title: 使用平台叫用封送處理資料
ms.date: 07/31/2018
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae8fbb47986e5baaecb919ce79ae384a8427737a
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "48850474"
---
# <a name="marshaling-data-with-platform-invoke"></a>使用平台叫用封送處理資料
若要呼叫從 Unmanaged 程式庫匯出的函式，.NET Framework 應用程式需要代表此 Unmanaged 函式之 Managed 程式碼中的函式原型。 若要建立使平台叫用正確地封送處理資料的原型，您必須執行下列動作：  
  
-   將 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性套用至使用 Managed 程式碼的靜態函式或方法。  
  
-   將 Unmanaged 資料類型替代為 Managed 資料類型。  
  
 您可以使用 Unmanaged 函式所提供的文件，以選擇性欄位套用屬性，並且將 Unmanaged 資料類型替代為 Managed 資料類型，來建構對等的 Managed 原型。 如需如何套用 **DllImportAttribute** 的指示，請參閱[使用 Unmanaged DLL 函式](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)。  
  
 本節提供範例，示範如何建立 Managed 函式原型，供傳遞引數至函式和接收 Unmanaged 程式庫所匯出函式的傳回值。 此範例也會示範使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性和 <xref:System.Runtime.InteropServices.Marshal> 類別來明確封送處理資料的時機。  
  
## <a name="platform-invoke-data-types"></a>平台叫用資料類型  
 下表列出 Win32 API (Wtypes.h 中所列) 和 C 樣式函式中所使用的資料類型。 許多 Unmanaged 程式庫包含傳遞資料類型做為參數和傳回值的函式。 第三個行列出對應的 .NET Framework 內建實值類型或您在 Managed 程式碼中使用的類別。 在某些情況下，您可將本表格中所列的類型取代為相同大小的類型。  
  
|在 Wtypes.h 中的 Unmanaged 類型|Unmanaged C 語言類型|Managed 類別名稱|描述|  
|--------------------------------|-------------------------------|------------------------|-----------------|  
|**VOID**|**void**|<xref:System.Void?displayProperty=nameWithType>|套用至未傳回值的函式。|
|**HANDLE**|**void \***|<xref:System.IntPtr?displayProperty=nameWithType>|在 32 位元 Windows 作業系統上為 32 位元，在 64 位元 Windows 作業系統上為 64 位元。|  
|**BYTE**|**unsigned char**|<xref:System.Byte?displayProperty=nameWithType>|8 位元|  
|**SHORT**|**short**|<xref:System.Int16?displayProperty=nameWithType>|16 位元|  
|**WORD**|**unsigned short**|<xref:System.UInt16?displayProperty=nameWithType>|16 位元|  
|**INT**|**int**|<xref:System.Int32?displayProperty=nameWithType>|32 位元|  
|**UINT**|**unsigned int**|<xref:System.UInt32?displayProperty=nameWithType>|32 位元|  
|**LONG**|**long**|<xref:System.Int32?displayProperty=nameWithType>|32 位元|  
|**BOOL**|**long**|<xref:System.Byte>|32 位元|  
|**DWORD**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32 位元|  
|**ULONG**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32 位元|  
|**CHAR**|**char**|<xref:System.Char?displayProperty=nameWithType>|使用 ANSI 裝飾。|  
|**WCHAR**|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|使用 Unicode 裝飾。|  
|**LPSTR**|**char &ast;**|<xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType>|使用 ANSI 裝飾。|  
|**LPCSTR**|**Const char &ast;**|<xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType>|使用 ANSI 裝飾。|  
|**LPWSTR**|**wchar_t &ast;**|<xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType>|使用 Unicode 裝飾。|  
|**LPCWSTR**|**Const wchar_t &ast;**|<xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType>|使用 Unicode 裝飾。|  
|**FLOAT**|**Float**|<xref:System.Single?displayProperty=nameWithType>|32 位元|  
|**DOUBLE**|**Double**|<xref:System.Double?displayProperty=nameWithType>|64 位元|  
  
 如需 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C# 和 C++ 中的對應類型，請參閱 [簡介](../../../docs/standard/class-library-overview.md)。  
  
## <a name="pinvokelibdll"></a>PinvokeLib.dll  
 下列程式碼定義 Pinvoke.dll 所提供的程式庫函式。 本節所描述的許多範例會呼叫此程式庫。  
  
### <a name="example"></a>範例  
 [!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]  
  
 [!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
