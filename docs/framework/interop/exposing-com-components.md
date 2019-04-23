---
title: 將 COM 元件公開給 .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b7aa028afeaf4230ee079f0d4071a5cd6a21c65
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320908"
---
# <a name="exposing-com-components-to-the-net-framework"></a>將 COM 元件公開給 .NET Framework
本節摘要說明向 Managed 程式碼公開現有 COM 元件所需要的程序。 如需撰寫與 .NET Framework 緊密整合的 COM 伺服器的詳細資訊，請參閱[交互操作的設計考量](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))。
  
 現有的 COM 元件是 Managed 程式碼中的寶貴資源，如同中介層商務應用程式或隔離功能。 理想的元件具有主要 Interop 組件，並能緊密貼合 COM 所加諸的程式設計標準。  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a>將 COM 元件公開給 .NET Framework  
  
1. [匯入型別程式庫作為組件](importing-a-type-library-as-an-assembly.md)。  
  
     Common Language Runtime 需要所有類型的中繼資料，包括 COM 類型。 有數種方式可以取得包含 COM 類型的組件，這些類型會匯入為中繼資料。  
  
2. [使用受控碼中的 COM 類型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))。  
  
     您可以檢查 COM 類型、啟動執行個體，以及使用您處理任何 Managed 類型的相同方式在 COM 物件上叫用方法。  
  
3. [編譯 Interop 專案](compiling-an-interop-project.md)。  
  
     [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 提供與 Common Language Specification (CLS) 相容的數種語言編譯器，包括 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C# 和 C++。  
  
4. [部署 Interop 應用程式](deploying-an-interop-application.md)。  
  
     Interop 應用程式最適合部署為全域組件快取中具有[強式名稱](../app-domains/strong-named-assemblies.md)的已簽署組件。  
  
## <a name="see-also"></a>另請參閱

- [與 Unmanaged 程式碼互通](index.md)
- [交互操作的設計考量](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))
- [COM Interop 範例：.NET 用戶端與 COM 伺服器](com-interop-sample-net-client-and-com-server.md)
- [語言獨立性以及與語言無關的元件](../../standard/language-independence-and-language-independent-components.md)
- [Gacutil.exe (全域組件快取工具)](../tools/gacutil-exe-gac-tool.md)
