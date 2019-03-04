---
title: 作法：建置多檔案組件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68f525244f2238ebdc44116fc91c3ddcb0a79bfd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975052"
---
# <a name="how-to-build-a-multifile-assembly"></a>作法：建置多檔案組件
本文說明如何建立多檔案組件，並提供說明程序中每個步驟的程式碼。

> [!NOTE]
> 適用於 C# 和 Visual Basic 的 Visual Studio IDE 只能用來建立單一檔案組件。 如果您想建立多檔案組件，則必須使用命令列編譯器或搭配 Visual C++ 使用 Visual Studio。

### <a name="to-create-a-multifile-assembly"></a>若要建立多檔案組件

01. 將所有檔案編譯為程式碼模組，該檔案所包含的命名空間將由組件的其他模組參考。 程式碼模組的預設副檔名為 .netmodule。

    例如，假設 `Stringer` 檔案有名為 `myStringer` 的命名空間，其中包括名為 `Stringer` 的類別。 `Stringer` 類別含有 `StringerMethod`，可撰寫單行到主控台。

    [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
    [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
    [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]

    請使用下列命令來編譯此程式碼：

    [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
    [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
    [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]

    使用 **/t:** 編譯器選項指定 *module* 參數，表示應將檔案編譯成模組，而非編譯成組件。 編譯器可產生稱為 `Stringer.netmodule` 的模組，您可以將它加入至組件。

02. 使用必要的編譯器選項來編譯其他所有模組，以便指出程式碼中所參考的其他模組。 這個步驟使用 **/addmodule** 編譯器選項。

    在下列範例中，名為 `Client` 的程式碼模組擁有進入點 `Main` 方法，該方法會參考步驟 1 建立的 `Stringer.dll` 模組方法。

    [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
    [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
    [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]

    請使用下列命令來編譯此程式碼：

    [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
    [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
    [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]

    請指定 **/t:module** 選項，因為這個模組將在下一個步驟中新增到組件。 請指定 **/addmodule** 選項，因為 `Client` 的程式碼會參考 `Stringer.netmodule` 的程式碼建立的命名空間。 編譯器會產生稱為 `Client.netmodule` 的模組，其中包含對另一個模組 `Stringer.netmodule` 的參考。

    >[!NOTE]
    >C# 和 Visual Basic 編譯器支援使用下列兩個不同的語法來直接建立多檔案組件。
    >
    >- 兩種編譯 (Compilation) 建立雙檔案組件：
    >
    >    [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
    >    [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
    >    [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]
    >
    >- 單一編譯建立雙檔案組件：
    >
    >    [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
    >    [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
    >    [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]

03. 使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 來建立輸出檔案，其中含有組件資訊清單。 這個檔案含有所有模組的參考資訊或者是部分組件的資源。

    在命令提示字元中輸入下列命令：

    **al** \<*模組名稱*> \<*模組名稱*> … **/main:**\<*方法名稱*> **/out:**\<*檔案名稱*> **/target:**\<*組件檔案類型*>

    在這個命令中，「模組名稱」引數會指定組件中包含的所有模組名稱。 **/main:** 選項指定方法名稱，這個名稱是組件的進入點。 **/out:** 選項指定輸出檔案的名稱，其中包含組件中繼資料。 **/target:** 選項指定組件為主控台應用程式可執行檔 (.exe)、Windows 可執行檔 (.win) 或程式庫 (.lib) 檔案。

    下列範例中，Al.exe 建立組件，該組件為 `myAssembly.exe` 主控台應用程式可執行檔。 該應用程式是由兩個稱為 `Client.netmodule` 和 `Stringer.netmodule` 的模組，以及僅包含組件中繼資料且稱為 `myAssembly.exe,` 的可執行檔所組成。 組件的進入點為 `Main` 類別的 `MainClientApp` 方法，位於 `Client.dll` 中。

    ```
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    您可以使用 [MSIL 反組譯工具 (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢查組件的內容，或判斷檔案為組件或模組。

## <a name="see-also"></a>另請參閱
- [建立組件](../../../docs/framework/app-domains/create-assemblies.md)
- [如何：檢視組件內容](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)
- [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [多檔案組件](../../../docs/framework/app-domains/multifile-assemblies.md)
