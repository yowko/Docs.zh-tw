---
title: 與非受控程式碼交互操作
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 583cfb6e3a5145c6c0dfc82ec9ff64c6d87414ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="interoperating-with-unmanaged-code"></a>與非受控程式碼交互操作

.NET Framework 可促進與 COM 元件、COM+ 服務、外部型別程式庫和許多作業系統服務進行的互動。 資料類型、方法簽章和錯誤處理機制因 Managed 和 Unmanaged 物件模型而有所不同。 為了簡化 .NET Framework 元件與 Unmanaged 程式碼之間的互通性，以及簡化移轉路徑，通用語言執行平台會對用戶端與伺服器隱匿這些物件模型中的差異。

在執行階段的控制之下執行的程式碼稱為 Managed 程式碼。 相反地，在執行階段外部執行的程式碼稱為 Unmanaged 程式碼。 COM 元件、ActiveX 介面及 Win32 API 函式都是 Unmanaged 程式碼的範例。

## <a name="in-this-section"></a>本節內容

[將 COM 元件公開給 .NET Framework](exposing-com-components.md)  
描述如何從 .NET Framework 應用程式使用 COM 元件。

[將 .NET Framework 元件公開給 COM](exposing-dotnet-components-to-com.md)  
描述如何從 COM 應用程式使用 .NET Framework 元件。

[使用 Unmanaged DLL 函式](consuming-unmanaged-dll-functions.md)  
描述如何使用平台叫用呼叫 Unmanaged DLL 函式。

[Interop 封送處理](interop-marshaling.md)  
描述適用於 COM Interop 和平台叫用的封送處理。

[操作說明：對應 HRESULT 和例外狀況](how-to-map-hresults-and-exceptions.md)  
描述例外狀況與 HRESULT 之間的對應。

[COM 包裝函式](com-wrappers.md)  
描述由 COM Interop 所提供的包裝函式。

[類型等價和內嵌 Interop 類型](type-equivalence-and-embedded-interop-types.md)  
描述如何將 COM 類型的類型資訊內嵌於組件，以及通用語言執行平台如何決定內嵌 COM 類型的對等項。

[如何：使用 Tlbimp.exe 產生主要 Interop 組件](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
描述如何使用 *Tlbimp.exe* (類型程式庫匯入工具) 產生主要 Interop 組件。

[如何：登錄主要 Interop 組件](how-to-register-primary-interop-assemblies.md)  
描述如何註冊主要 Interop 組件，以便您能在專案中加以參考。

[免註冊的 COM Interop](registration-free-com-interop.md)  
描述 COM Interop 如何在不使用 Windows 登錄的情況下啟動元件。

[如何：設定免註冊啟用的 .NET Framework 架構 COM 元件](configure-net-framework-based-com-components-for-reg.md)  
描述如何建立應用程式資訊清單，以及如何建立和內嵌元件資訊清單。
