---
title: Managed 執行程序
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- source code language
- code, managed execution process
- runtime, managed execution process
- compiling source code, managed execution process
- managed execution process
- common language runtime, managed execution process
ms.assetid: 476b03dc-2b12-49a7-b067-41caeaa2f533
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d11567b3a5abca6e81ff0358295aa8516ef6443f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969022"
---
# <a name="managed-execution-process"></a>Managed 執行程序
<a name="introduction"></a> Managed 執行處理序包含下列步驟，將於本主題中稍後詳細討論：  
  
1. [選擇編譯器](#choosing_a_compiler)。  
  
     若要享有 Common Language Runtime 帶來的好處，您必須使用一個或多個以執行階段為目標的語言編譯器。  
  
2. [編譯您的程式碼為 MSIL](#compiling_to_msil)。  
  
     編譯會將您的原始程式碼轉譯成 Microsoft 中間語言 (MSIL)，並產生必要的中繼資料。  
  
3. [將 MSIL 編譯成機器碼](#compiling_msil_to_native_code)。  
  
     在執行期間，Just-In-Time (JIT) 編譯器會將 MSIL 轉譯成機器碼。 在這個編譯期間，程式碼必須通過驗證程序，這會檢查 MSIL 和中繼資料，以了解是否可判斷程式碼為類型安全的。  
  
4. [執行程式碼](#running_code)。  
  
     Common Language Runtime 提供基礎結構，啟用執行以及可在執行期間使用的服務。  
  
<a name="choosing_a_compiler"></a>   
## <a name="choosing-a-compiler"></a>選擇編譯器  
 若要享有 Common Language Runtime (CLR) 帶來的好處，就必須使用一個或多個以執行階段為目標的語言編譯器，例如 Visual Basic、C#、Visual C++、F#，或眾多協力廠商編譯器的其中一種，例如 Eiffel、Perl 或 COBOL 編譯器。  
  
 因為是多種程式語言的執行環境，執行階段會支援各種資料類型和語言功能。 您使用的語言編譯器將決定有哪些執行階段功能可用，而您可使用那些功能來設計程式碼。 編譯器會建立程式碼必須使用的語法，而不是由執行階段建立。 如果您的元件必須完全可用於其他語言撰寫的元件，元件的匯出類型必須只公開包含在 [Language Independence and Language-Independent Components](../../docs/standard/language-independence-and-language-independent-components.md) (CLS) 中的語言功能。 您可以使用 <xref:System.CLSCompliantAttribute> 屬性來確保您的程式碼符合 CLS 標準。 如需詳細資訊，請參閱 [Language Independence and Language-Independent Components](../../docs/standard/language-independence-and-language-independent-components.md)。  
  
 [回到頁首](#introduction)  
  
<a name="compiling_to_msil"></a>   
## <a name="compiling-to-msil"></a>編譯為 MSIL  
 編譯為 Managed 程式碼時，編譯器會將您的原始程式碼轉譯成 Microsoft 中間語言 (MSIL)，這是一種與 CPU 無關的指令集，可以有效率地轉換為機器碼。 MSIL 包括可用來載入、儲存、初始化和呼叫物件上方法的指令，以及用於算術和邏輯運算、控制流程、直接記憶體存取、例外處理和其他作業的指令。 在程式碼可以執行之前，必須將 MSIL 轉換為 CPU 特定程式碼，而此轉換通常是由 [Just-In-Time (JIT) 編譯器](#compiling_msil_to_native_code)進行。 由於 Common Language Runtime 會為其支援的每一個電腦架構提供一個或多個 JIT 編譯器，因此相同的 MSIL 集可以在任何受支援的架構上進行 JIT 編譯並執行。  
  
 當編譯器產生 MSIL 時，它也會產生中繼資料。 中繼資料描述您程式碼中的類型，包括各個類型的定義、各個類型成員的簽章、您的程式碼所參考的成員，和執行階段在執行期間使用的其他資料。 MSIL 和中繼資料會包含在可攜式執行 (PE) 檔中，該檔案根據已發行的 Microsoft PE，以及過去供可執行檔內容使用的通用物件檔案格式 (COFF) 為基礎並對這些加以擴充。 這種檔案格式 (適用於 MSIL 或機器碼以及中繼資料) 使作業系統能夠辨認 Common Language Runtime 的映像。 檔案內存在的中繼資料連同 MSIL 讓您的程式碼能夠描述自己，也就是說，不需要類型程式庫或介面定義語言 (IDL)。 此執行階段視需要會在執行期間從檔案找出中繼資料並擷取。  
  
 [回到頁首](#introduction)  
  
<a name="compiling_msil_to_native_code"></a>   
## <a name="compiling-msil-to-native-code"></a>將 MSIL 編譯成機器碼  
 Microsoft 中間語言 (MSIL) 必須先根據 Common Language Runtime 編譯成機器碼才能執行 (該程式碼是根據目標電腦架構來編譯)。 .NET Framework 提供兩種執行這項轉換的方式：  
  
- .NET Framework Just-In-Time (JIT) 編譯器。  
  
- .NET Framework [Ngen.exe (原生映像產生器)](../../docs/framework/tools/ngen-exe-native-image-generator.md)。  
  
### <a name="compilation-by-the-jit-compiler"></a>使用 JIT 編譯器編譯  
 當載入和執行組件內容時，JIT 編譯會視需要於應用程式執行階段將 MSIL 轉換成機器碼。 由於 Common Language Runtime 會為每個支援的 CPU 架構提供 JIT 編譯器，因此開發人員可以建置可在不同架構的電腦上進行 JIT 編譯和執行的 MSIL 組件集。 然而，如果您的 Managed 程式碼呼叫特定平台的原生 API 或特定平台的類別庫，便只能在特定的作業系統上執行。  
  
 JIT 編譯還會考慮到在執行期間可能永遠不會呼叫某些程式碼。 它並不耗用時間和記憶體將可攜式執行檔中所有的 MSIL 轉換為機器碼，而是在執行期間視需要轉換 MSIL 並在記憶體中儲存產生的機器碼，以供該處理序內容中的後續呼叫存取。 載入類型並初始化時，載入器會建立虛設常式並附加至類型中的每一個方法。 初次呼叫方法時，虛設常式會將控制項傳遞至 JIT 編譯器，該編譯器會將此方法的 MSIL 轉換成機器碼，並且修改虛設常式為直接指向產生的機器碼。 因此，JIT 編譯方法的後續呼叫會直接移至機器碼。  
  
### <a name="install-time-code-generation-using-ngenexe"></a>使用 NGen.exe 產生安裝期間程式碼  
 由於 JIT 編譯器會在呼叫該組件中所定義的個別方法時，將組件的 MSIL 轉換成機器碼，因此這會對執行階段的效能產生不良影響。 在大部分情況下，效能稍減是可以接受的。 最重要的是，JIT 編譯器產生的程式碼會繫結至觸發編譯的處理序。 該程式碼無法跨多個處理序共用。 為了允許在多個應用程式的引動過程間共用產生的程式碼，或允許在共用組件集的多個處理序間共用產生的程式碼，Common Language Runtime 支援事先編譯模式。 這個預先編譯模式會使用 [Ngen.exe (原生映像產生器)](../../docs/framework/tools/ngen-exe-native-image-generator.md) 將 MSIL 組件轉換成機器碼，與 JIT 編譯器相當類似。 不過，Ngen.exe 的作業與 JIT 編譯器的作業有三個不同的地方：  
  
- 它會事先執行從 MSIL 至機器碼的轉換，而不是在執行應用程式時。  
  
- 它會一次編譯整個組件，而非一次一個方法。  
  
- 它會將原生映像快取中產生的程式碼保存為磁碟上的檔案。  
  
### <a name="code-verification"></a>程式碼驗證  
 做為編譯成機器碼過程的一部分，MSIL 程式碼必須通過驗證程序，除非系統管理員建立的安全性原則允許程式碼略過驗證。 驗證會檢查 MSIL 和中繼資料，以了解該程式碼是否為類型安全，表示它僅存取獲得授權之可存取的記憶體位置。 類型安全有助於隔離各物件，因此就能免於意外或惡意的損毀。 它也保證會確實地強制執行程式碼的安全性限制。  
  
 可驗證的類型安全程式碼會滿足下列陳述，此為執行階段所仰賴的：  
  
- 類型的參考與正被參考的類型完全相容。  
  
- 在物件上只叫用適當定義的作業。  
  
- 這些識別與它們所宣告的一樣。  
  
 在驗證程序期間，會檢查 MSIL 程式碼以確認程式碼只會使用正確定義的類型來存取記憶體位置和呼叫方法。 例如，程式碼不允許以可讓記憶體位置滿溢的方式存取物件欄位。 此外，驗證會檢視程式碼，以判斷 MSIL 是否已經正確產生，因為不正確的 MSIL 可能會違反類型安全規則。 驗證程序會讓妥善定義的類型安全程式碼集合通過驗證，它也只會讓類型安全的程式碼通過驗證。 然而，由於驗證程序的某些限制，某些類型安全程式碼可能無法通過驗證，而某些語言由於設計之故，不會產生可驗證的類型安全程式碼。 如果安全性原則需要類型安全程式碼，但該程式碼沒有通過驗證，則在程式碼執行時會產生例外狀況。  
  
 [回到頁首](#introduction)  
  
<a name="running_code"></a>   
## <a name="running-code"></a>執行程式碼  
 Common Language Runtime 提供基礎結構，啟用 Managed 執行以及可在執行期間使用的服務。 在可以執行方法之前，必須將其編譯為處理器特定程式碼。 在初次呼叫時，已經產生 MSIL 的每個方法都會進行 JIT 編譯，然後才會執行。 下次執行方法時，就會執行現有以 JIT 編譯的機器碼。 JIT 編譯和接著執行程式碼的過程會不斷重複，直到執行完成為止。  
  
 在執行期間，Managed 程式碼會接收服務，例如記憶體回收、安全性、與 Unmanaged 程式碼的互通性、跨語言偵錯支援，以及增強的部署和版本控制支援。  
  
 在 Microsoft [!INCLUDE[winxp](../../includes/winxp-md.md)] 和 [!INCLUDE[windowsver](../../includes/windowsver-md.md)]中，作業系統載入器會查看 COFF 標頭中的位元，檢查 Managed 模組。 所設定的位元代表 Managed 模組。 如果載入器偵測到 Managed 模組，則會載入 mscoree.dll，而當載入和卸載 Managed 模組映像時， `_CorValidateImage` 和 `_CorImageUnloading` 會通知載入器。 `_CorValidateImage` 會執行下列動作：  
  
1. 確定程式碼是有效的 Managed 程式碼。  
  
2. 將映像中的進入點變更為執行階段中的進入點。  
  
 在 64 位元的 Windows 中， `_CorValidateImage` 會將記憶體中的映像從 PE32 格式轉換為 PE32+ 格式，以便進行修改。  
  
 [回到頁首](#introduction)  
  
## <a name="see-also"></a>另請參閱

- [概觀](../../docs/framework/get-started/overview.md)
- [語言獨立性以及與語言無關的元件](../../docs/standard/language-independence-and-language-independent-components.md)
- [中繼資料和自我描述元件](../../docs/standard/metadata-and-self-describing-components.md)
- [Ilasm.exe (IL 組譯工具)](../../docs/framework/tools/ilasm-exe-il-assembler.md)
- [Security](../../docs/standard/security/index.md)
- [與 Unmanaged 程式碼互通](../../docs/framework/interop/index.md)
- [部署](../../docs/framework/deployment/net-framework-applications.md)
- [.NET 中的組件](assembly/index.md)
- [應用程式定義域](../../docs/framework/app-domains/application-domains.md)
