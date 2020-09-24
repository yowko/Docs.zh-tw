---
title: 互通性概觀 - C# 程式設計指南
description: '瞭解 c # 與非受控碼之間的互通性，包括平台叫用、c + + interop、將 COM 元件公開給 c #，以及將 c # 公開給 COM。'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: f05c53eec326517052eb9a46e57e8b9c18ea698f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149682"
---
# <a name="interoperability-overview-c-programming-guide"></a>互通性概觀 (C# 程式設計手冊)

本主題說明可在 C# Managed 程式碼和 Unmanaged 程式碼之間啟用互通性的方法。  
  
## <a name="platform-invoke"></a>平台叫用  

 *平台叫用*服務，可讓 Managed 程式碼呼叫 Unmanaged 函式在動態連結程式庫 (DLL) 中實作，例如 Microsoft Windows API 中。 它會找出並叫用匯出的函式，並且在需要的時候於交互操作界限之間封送處理其引數 (整數、 字串、 陣列、 結構和其他) 。  
  
如需詳細資訊，請參閱使用 [非受控 DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md) 函式，以及 [如何使用平台叫用播放 WAV](./how-to-use-platform-invoke-to-play-a-wave-file.md)檔。
  
> [!NOTE]
> [Common Language Runtime](../../../standard/clr.md) (CLR) 管理對系統資源的存取。 在 CLR 外部呼叫 Unmanaged 程式碼會略過此安全性機制，因而造成安全性風險。 例如，Unmanaged 程式碼可能會直接呼叫 Unmanaged 程式碼中的資源，並略過 CLR 安全性機制。 如需詳細資訊，請參閱 [.NET 的安全性](../../../standard/security/index.md)。  
  
## <a name="c-interop"></a>C++ Interop  

 您可以使用 c + + interop （也稱為 (IJW) ）包裝原生 c + + 類別，讓以 c # 或其他 .NET 語言撰寫的程式碼可以使用它。 若要這樣做，您可以撰寫 C++ 程式碼來包裝原生 DLL 或 COM 元件。 與其他 .NET 語言不同的是，Visual C++ 具有互通性支援，可讓 managed 和非受控程式碼位於相同的應用程式中，甚至在相同的檔案中。 您接著可使用 **/clr** 編譯器參數建立 C++ 程式碼，以產生 Managed 組件。 最後，您可以在 C# 專案中新增組件的參考，並使用包裝的物件，就像是使用其他 Managed 類別一樣。  
  
## <a name="exposing-com-components-to-c"></a>將 COM 元件公開給 C\#

 您可以從 C# 專案取用 COM 元件。 一般步驟如下所示：  
  
1. 找出並註冊所要使用的 COM 元件。 使用 regsvr32.exe 註冊或取消註冊 COM DLL。  
  
2. 將 COM 元件或型別程式庫的參考新增至專案。  
  
     當您加入參考時，Visual Studio 使用 [Tlbimp.exe (型別程式庫匯入工具) ](../../../framework/tools/tlbimp-exe-type-library-importer.md)，它會採用類型程式庫做為輸入，以輸出 .net interop 元件。 此組件 (也稱為執行階段可呼叫包裝函式 (RCW)) 包含 Managed 類別和介面，以包裝型別程式庫中的 COM 類別和介面。 Visual Studio 會將產生的組件參考新增至專案。  
  
3. 建立定義於 RCW 之類別的執行個體。 這會接著建立 COM 物件的執行個體。  
  
4. 就像是使用其他 Managed 物件一樣來使用此物件。 當記憶體回收將物件回收時，也會從記憶體釋放 COM 物件的執行個體。  
  
 如需詳細資訊，請參閱[將 COM 元件公開給 .NET Framework](../../../framework/interop/exposing-com-components.md)。  
  
## <a name="exposing-c-to-com"></a>將 C# 公開給 COM  

 COM 用戶端可取用已正確公開的 C# 類型。 公開 C# 類型的基本步驟如下所示：  
  
1. 在 C# 專案中新增 Interop 屬性。  
  
     您可以藉由修改 Visual C# 專案屬性來顯示組件 COM。 如需詳細資訊，請參閱[組件資訊對話方塊](/visualstudio/ide/reference/assembly-information-dialog-box)。  
  
2. 產生 COM 型別程式庫並註冊供 COM 使用。  
  
     您可以修改 Visual C# 專案屬性，以自動為 COM Interop 註冊 C# 組件。 Visual Studio 使用 [Regasm.exe (組件登錄工具)](../../../framework/tools/regasm-exe-assembly-registration-tool.md)，並使用接受受控組件作為輸入的 `/tlb` 命令列參數，以產生型別程式庫。 此型別程式庫描述組件中的 `public` 類型，並新增登錄項目，讓 COM 用戶端可以建立 Managed 類別。  
  
 如需詳細資訊，請參閱[將 .NET Framework 元件公開給 COM](../../../framework/interop/exposing-dotnet-components-to-com.md) 和[範例 COM 類別](./example-com-class.md)。  
  
## <a name="see-also"></a>另請參閱

- [提升 Interop 效能](/previous-versions/msp-n-p/ff647812(v=pandp.10))
- [COM 和.NET 之間的互通性簡介](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [Visual Basic 中的 COM Interop 簡介](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [在受控碼和非受控碼之間進行封送處理](../../../framework/interop/interop-marshaling.md)
- [與 Unmanaged 程式碼互通](../../../framework/interop/index.md)
- [C # 程式設計指南](../index.md)
