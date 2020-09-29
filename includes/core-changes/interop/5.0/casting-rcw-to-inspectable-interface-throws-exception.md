---
ms.openlocfilehash: 8693c1fdef5fa194b16127d4f1dd87e23ad68f2d
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438045"
---
### <a name="casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception"></a>將 RCW 轉換成介面會擲回 `InterfaceIsIInspectable` PlatformNotSupportedException

將執行時間可呼叫包裝函式 (RCW) 轉換為標示為的介面，現在會擲回 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> <xref:System.PlatformNotSupportedException> 。 這項變更是 [從 .net 移除 WinRT 支援](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net)的後續變更。

#### <a name="version-introduced"></a>引進的版本

5.0 RC2

#### <a name="change-description"></a>變更描述

在 .net 5.0 preview 6 之前的 .NET 版本中，將 RCW 轉換為標示為如 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 預期般運作的介面。 在 .NET 5.0 預覽版6-8 和 RC1 中，您可以成功地將 RCW 轉換成 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 介面。 不過，當您在介面上執行方法時，您可能會發生存取違規，因為執行時間中的基礎支援 [已在 .net 5.0 preview 6 中移除](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net)。

在 .NET 5.0 RC2 和更新版本中，將 RCW 轉換成標記為的介面會 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> <xref:System.PlatformNotSupportedException> 在轉換時間擲回。

#### <a name="reason-for-change"></a>變更的原因

的支援 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 已 [在先前的 .net 5.0 preview 中移除](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net)。 但是， <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 不小心會忽略轉換成介面的。 因為執行時間中的基礎支援已不存在，所以擲回會 <xref:System.PlatformNotSupportedException> 啟用正常失敗路徑。 擲回例外狀況也可讓您更容易發現這項功能已不再受到支援。

#### <a name="recommended-action"></a>建議的動作

- 如果您可以在 Windows 執行時間中繼資料中定義介面 (WinMD) 檔，請改用 c #/WinRT 工具。

- 否則，請將介面標示為 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> 而不是 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> ，然後將三個虛擬專案加入至方法的介面開頭 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 。 下列程式碼片段顯示範例。

  ```csharp
  [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
  interface IMine
  {
      // Do not call these three methods.
      // They're exclusively to fill in the slots in the vtable.
      void GetIIdsSlot();
      void GetRuntimeClassNameSlot();
      void GetTrustLevelSlot();

      // The original members of the IMine interface go here.
      ...
  }
  ```

#### <a name="category"></a>類別

Interop

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable`

-->
