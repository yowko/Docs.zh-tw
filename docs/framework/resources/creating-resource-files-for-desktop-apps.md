---
title: 建立 .NET 應用程式的資源檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resources files
- .resources files
- application resources, creating files
- resource files, creating
ms.assetid: 6c5ad891-66a0-4e7a-adcf-f41863ba6d8d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7ff34285220fd1e3c17503a8387104e91ec08b1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313654"
---
# <a name="create-resource-files-for-net-apps"></a>建立 .NET 應用程式的資源檔

您可以在資源檔中包括資源 (例如字串、影像或物件資料)，以讓應用程式輕鬆地使用它們。 .NET Framework 提供五種方式來建立資源檔：

- 建立包含字串資源的文字檔。 您必須使用[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 將文字檔轉換成二進位資源 (.resources) 檔案。 您接著可以使用語言編譯器將二進位資源檔內嵌在應用程式可執行檔或應用程式程式庫中，或使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。 如需詳細資訊，請參閱[文字檔中的資源](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#TextFiles)一節。

- 建立包含字串、影像或物件資料的 XML 資源 (.resx) 檔案。 您必須使用[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 將 .resx 檔案轉換成二進位資源檔 (.resources)。 您接著可以使用語言編譯器將二進位資源檔內嵌在應用程式可執行檔或應用程式程式庫中，或使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。 如需詳細資訊，請參閱 [.resx 檔案中的資源](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResxFiles)一節。

- 使用 <xref:System.Resources> 命名空間中的類型，以程式設計方式建立 XML 資源檔 (.resx)。 您可以建立 .resx 檔案、列舉其資源，並依名稱擷取特定資源。 如需詳細資訊，請參閱[以程式設計方式使用 .resx 檔案](../../../docs/framework/resources/working-with-resx-files-programmatically.md)主題。

- 以程式設計方式建立二進位資源檔 (.resources)。 您接著可以使用語言編譯器將檔案內嵌在應用程式可執行檔或應用程式程式庫中，或使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。 如需詳細資訊，請參閱 [.resources 檔案中的資源](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles)一節。

- 使用 [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 建立資源檔，並將它包含在您的專案中。 Visual Studio 提供可讓您新增、刪除和修改資源的資源編輯器。 在編譯時間，資源檔會自動轉換成二進位 .resources 檔案，並內嵌在應用程式組件或附屬組件中。 如需詳細資訊，請參閱 [Visual Studio 中的資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles)一節。

<a name="TextFiles"></a>
## <a name="resources-in-text-files"></a>文字檔中的資源

您只能使用文字 (.txt 或 .restext) 檔案來儲存字串資源。 針對非字串資源，請使用 .resx 檔案或以程式設計方式建立它們。 包含字串資源的文字檔的格式如下：

```text
# This is an optional comment.
name = value

; This is another optional comment.
name = value

; The following supports conditional compilation if X is defined.
#ifdef X
name1=value1
name2=value2
#endif

# The following supports conditional compilation if Y is undefined.
#if !Y
name1=value1
name2=value2
#endif
```

 .txt 和 .restext 檔案的資源檔格式完全相同。 .restext 副檔名只提供可立即將文字檔識別為文字資源檔。

 字串資源會以「名稱/值」配對的形式出現，其中「名稱」是識別資源的字串，「值」則是當您將「名稱」傳遞至資源擷取方法 (例如 <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>) 時所傳回的資源字串。 「名稱」和「值」必須以等號 (=) 分隔。 例如：

```text
FileMenuName=File
EditMenuName=Edit
ViewMenuName=View
HelpMenuName=Help
```

> [!CAUTION]
> 請勿使用資源檔儲存密碼、安全機密資訊或私用資料。

 文字檔中允許空字串 (即其值為 <xref:System.String.Empty?displayProperty=nameWithType> 的資源)。 例如：

```
EmptyString=
```

 從 .NET Framework 4.5 及所有版本的 .NET Core 開始，文字檔案支援使用 `#ifdef` 符號... `#endif` 及 `#if !` 符號... `#endif` 建構的條件式編譯。 您接著可以搭配使用 `/define` 切換參數與[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 來定義符號。 每個資源都需要自己的 `#ifdef`*symbol*... `#endif` 或 `#if !`*symbol*... `#endif` 建構。 如果您使用 `#ifdef` 陳述式而且已定義 *symbol*，則 .resources 檔案中會包括相關聯的資源；否則就不會包括該資源。 如果您使用 `#if !` 陳述式而且未定義 *symbol*，則 .resources 檔案中會包括相關聯的資源；否則就不會包括該資源。

 註解在文字檔中是選擇性的，並在行首加上分號 (;) 或井字號 (#)。 包含註解的程式行可以放在檔案中的任何地方。 使用[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 建立的已編譯 .resources 檔案中未包括註解。

 文字檔中的任何空白列都會視為空白字元，並且予以忽略。

 下列範例定義兩個名為 `OKButton` 和 `CancelButton` 的字串資源。

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 如果文字檔包含重複出現的「名稱」，則[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 會顯示警告，並忽略另一個名稱。

 「值」不可包含新行字元，但是您可以使用類似 C 語言逸出字元 (例如 `\n`) 代表新行，以及使用 `\t` 代表定位點。您也可以包括已逸出的反斜線字元 (例如，"\\\\")。 此外，也允許空字串。

 您應該在位元組由小到大或由大到小的位元組順序中使用 UTF-8 編碼或 UTF-16 編碼，以將資源儲存為文字檔格式。 不過，可將 .txt 檔案轉換為 .resources 檔案的[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，預設會將檔案視為 UTF-8。 如果您想要 Resgen.exe 辨識使用 UTF-16 所編碼的檔案，必須在檔案開頭包括 Unicode 位元組順序標記 (U+FEFF)。

 若要將文字格式的資源檔內嵌至 .NET 組件，您必須使用[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，將檔案轉換成二進位資源 (.resource) 檔。 您接著可以使用語言編譯器將 .resources 檔案內嵌在 .NET 組件中，或使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。

 下列範例針對簡單 "Hello World" 主控台應用程式使用名為 GreetingResources.txt 且為文字格式的資源檔。 文字檔會定義 `prompt` 和 `greeting` 這兩個字串，提示使用者輸入其名稱並顯示問候語。

```text
# GreetingResources.txt
# A resource file in text format for a "Hello World" application.
#
# Initial prompt to the user.
prompt=Enter your name:
# Format string to display the result.
greeting=Hello, {0}!
```

使用下列命令，以將文字檔轉換成 .resources 檔案：

```console
resgen GreetingResources.txt
```

 下列範例顯示主控台應用程式的原始程式碼，而主控台應用程式使用 .resources 檔案向使用者顯示訊息。

 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]

 如果您使用 Visual Basic，而且原始程式碼檔案命名為 Greeting.vb，則下列命令會建立包含內嵌 .resources 檔案的可執行檔：

```console
vbc greeting.vb -resource:GreetingResources.resources
```

 如果您使用 C#，而且原始程式碼檔案命名為 Greeting.cs，則下列命令會建立包含內嵌 .resources 檔案的可執行檔：

 ```console
csc greeting.cs -resource:GreetingResources.resources
```

<a name="ResxFiles"></a>
## <a name="resources-in-resx-files"></a>.resx 檔案中的資源
 與只能儲存字串資源的文字檔不同，XML 資源檔 (.resx) 可以儲存字串；影像、圖示和音訊剪輯這類二進位資料，以及程式化物件。 .resx 檔案包含描述資源項目格式的標準標頭，並指定用來剖析資料之 XML 的版本資訊。 資源檔資料接在 XML 標頭後面。 每個資料項目都會包含 `data` 標記中所含的名稱/值配對。 其 `name` 屬性定義資源名稱，而巢狀 `value` 標記包含資源值。 針對字串資料，`value` 標記會包含字串。

 例如，下列 `data` 標記會定義名為 `prompt` 且其值為 "Enter your name:" 的字串資源。

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> 請勿使用資源檔儲存密碼、安全機密資訊或私用資料。

 針對資源物件，**data** 標記會包括 `type` 屬性，以指出資源資料類型。 針對包含二進位資料的物件，`data` 標記也會包括 `mimetype` 屬性，以指出二進位資料的 `base64` 類型。

> [!NOTE]
> 所有 .resx 檔案都會使用二進位序列化格式子產生和剖析所指定類型的二進位資料。 因此，如果物件的二進位序列化格式以不相容的方式變更，則 .resx 檔案可能會無效。

 下列範例顯示 .resx 檔案中包括 <xref:System.Int32> 資源和點陣圖影像的一部分。

```xml
<data name="i1" type="System.Int32, mscorlib">
  <value>20</value>
</data>

<data name="flag" type="System.Drawing.Bitmap, System.Drawing,
    Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
    mimetype="application/x-microsoft.net.object.bytearray.base64">
  <value>
    AAEAAAD/////AQAAAAAAAAAMAgAAADtTeX…
  </value>
</data>
```

> [!IMPORTANT]
> 因為 .resx 檔案必須包含具有預先定義格式的格式正確 XML，所以不建議手動使用 .resx 檔案，特別是 .resx 檔案包含字串以外的資源時。 [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 改為提供一種透明的介面，來建立和操作 .resx 檔案。 如需詳細資訊，請參閱 [Visual Studio 中的資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles)一節。 您也可以透過程式設計方式建立和操作 .resx 檔案。 如需詳細資訊，請參閱[以程式設計方式使用 .resx 檔案](../../../docs/framework/resources/working-with-resx-files-programmatically.md)。

<a name="ResourcesFiles"></a>
## <a name="resources-in-resources-files"></a>.resources 檔案中的資源

您可以使用 <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> 類別，以程式設計方式直接從程式碼建立二進位資源檔 (.resources)。 您也可以使用[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，從文字檔或 .resx 檔案建立 .resources 檔案。 除了字串資料之外，.resources 檔案還可以包含二進位資料 (位元組陣列) 和物件資料。 以程式設計方式建立 .resources 檔案，需要下列步驟：

1. 建立具有唯一檔案名稱的 <xref:System.Resources.ResourceWriter> 物件。 做法是將檔案名稱或檔案資料流指定給 <xref:System.Resources.ResourceWriter> 類別建構函式。

2. 針對要新增至檔案的每個具名資源，呼叫 <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> 方法的其中一個多載。 資源可以是字串、物件或二進位資料集合 (位元組陣列)。

3. 呼叫 <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> 方法，以將資源寫入至檔案，並關閉 <xref:System.Resources.ResourceWriter> 物件。

> [!NOTE]
> 請勿使用資源檔儲存密碼、安全機密資訊或私用資料。

 下列範例會以程式設計方式建立名為 CarResources.resources 的 .resources 檔案，其中儲存六個字串、一個圖示和兩個應用程式定義的物件 (兩個 `Automobile` 物件)。 請注意，在此範例中定義和執行個體化的 `Automobile` 類別會標上 <xref:System.SerializableAttribute> 屬性，以讓二進位序列化格式子保存它。

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 當您建立 .resources 檔案之後，可以包括語言編譯器的 `/resource` 切換參數以將它內嵌在執行階段可執行檔或程式庫中，或是使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。

<a name="VSResFiles"></a>
## <a name="resource-files-in-visual-studio"></a>Visual Studio 中的資源檔

當您將資源檔新增至 [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 專案時，Visual Studio 會在專案目錄中建立 .resx 檔案。 Visual Studio 提供可讓您新增字串、影像和二進位物件的資源編輯器。 因為編輯器設計成只處理靜態資料，所以無法使用它們來儲存程式化物件；您必須以程式設計方式將物件資料寫入 .resx 檔案或 .resources 檔案。 如需詳細資訊，請參閱[以程式設計方式使用 .resx 檔案](../../../docs/framework/resources/working-with-resx-files-programmatically.md)和 [.resources 檔案中的資源](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles)章節。

若您要新增當地語系化的資源，請提供它們與主要資源檔相同的根檔案名稱。 您也應在檔案名稱中指定它們的文化特性 (Culture)。 例如，如果您新增名為 Resources.resx 的資源檔，也可能會建立名為 Resources.en-US.resx 和 Resources.fr-FR.resx 的資源檔，來分別保留英文 (美國) 和法文 (法國) 文化特性的當地語系化資源。 您也應該指定應用程式的預設文化特性。 如果找不到特定文化特性的當地語系化資源，則這是使用其資源的文化特性。 若要指定預設文化特性，請在 Visual Studio 的方案總管中以滑鼠右鍵按一下專案名稱、指向 [應用程式]、按一下 [組件資訊]，然後在 [中性語言] 清單中選取適當語言/文化特性。

在編譯時間，Visual Studio 先將專案中的 .resx 檔案轉換成二進位資源檔 (.resources)，並將它們儲存在專案 *obj* 目錄的子目錄中。 Visual Studio 會將未包含當地語系化資源的任何資源檔內嵌在專案所產生的主要組件中。 如果任何資源檔包含當地語系化資源，Visual Studio 會將其內嵌在每個當地語系化文化特性的個別附屬組件中。 它接著會將每個附屬組件儲存在名稱對應至當地語系化文化特性的目錄中。 例如，當地語系化的英文 (美國) 資源會儲存在 en-US 子目錄的附屬組件中。

## <a name="see-also"></a>另請參閱

- <xref:System.Resources>
- [桌面應用程式中的資源](../../../docs/framework/resources/index.md)
- [封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
