---
title: Ildasm.exe (IL 反組譯工具)
ms.date: 03/30/2017
helpviewer_keywords:
- PE files, MSIL Disassembler
- portable executable files, MSIL Disassembler
- Ildasm.exe
- MSIL Disassembler
- text files produced by MSIL Disassembler
- disassembling file for MSIL Assembler input
ms.assetid: db27f6b2-f1ec-499e-be3a-7eecf95ca42b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95a060f047094d7f1336a3e1e26b34c7d47b5a42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495510"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (IL 反組譯工具)

IL 反組譯工具是 IL 組譯工具 (*Ilasm.exe*) 的附屬工具。 *Ildasm.exe* 採用包含中繼語言 (IL) 程式碼的可攜式執行檔 (PE)，並建立適合用作 *Ilasm.exe* 輸入的文字檔。

此工具會自動與 Visual Studio 一起安裝。 若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。

在命令提示字元下輸入下列命令：

## <a name="syntax"></a>語法

```
ildasm [options] [PEfilename] [options]
```

#### <a name="parameters"></a>參數

下列選項可用於 *.exe*、*.dll*、*.obj*、*.lib* 和 *.winmd* 檔案。

| 選項 | 說明 |
| ------ | ----------- |
|**/out=** `filename`|建立具有指定 `filename` 的輸出檔案，而不是在圖形化使用者介面中顯示結果。|
|**/rtf**|產生 Rich Text Format (RTF) 格式的輸出。 使用 **/text** 選項時無效。|
|**/text**|在主控台視窗中顯示結果，而不是在圖形化使用者介面中顯示或做為輸出檔。|
|**/html**|產生 HTML 格式的輸出。 使用 **/output** 選項時才有效。|
|**/?**|顯示工具的命令語法和選項。|

下列其他選項可用於 *.exe*、*.dll* 和 *.winmd* 檔案。

| 選項 | 說明 |
| ------ | ----------- |
|**/bytes**|顯示十六進位格式的實際位元組做為指令註解。|
|**/caverbal**|以動詞化格式產生自訂屬性 BLOB。 預設為二進位格式。|
|**/linenum**|包含原始程式行的參考。|
|**/nobar**|隱藏反組譯碼進度指示器快顯視窗。|
|**/noca**|隱藏自訂屬性的輸出。|
|**/project**|以對 Managed 程式碼顯示的方式顯示中繼資料，而不採用在原生 [!INCLUDE[wrt](../../../includes/wrt-md.md)]中顯示的方式。 如果 `PEfilename` 不是 Windows 中繼資料 (*.winmd*) 檔案，這個選項就沒有任何作用。 請參閱[適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)。|
|**/pubonly**|僅反組譯公用類型和成員。 相當於 **/visibility:PUB**。|
|**/quoteallnames**|將所有名稱包含在單引號內。|
|**/raweh**|以未經處理格式顯示例外狀況處理子句。|
|**/source**|將原來的原始程式行顯示成註解。|
|**/tokens**|顯示類別和成員的中繼資料語彙基元。|
|**/visibility:** `vis`[+`vis`...]|僅反組譯具有所指定可視性的類型或成員。 以下是 `vis` 的有效值：<br /><br /> **PUB**：公開<br /><br /> **PRI**：私用<br /><br /> **FAM**：家族<br /><br /> **ASM**：組件<br /><br /> **FAA**：家族和組件<br /><br /> **FOA**：家族或組件<br /><br /> **PSC**：私用範圍<br /><br /> 如需這些可視性修飾詞的定義，請參閱 <xref:System.Reflection.MethodAttributes> 和 <xref:System.Reflection.TypeAttributes>。|

下列選項只對檔案或主控台輸出的 *.exe*、*.dll* 和 *.winmd* 檔案有效。

| 選項 | 說明 |
| ------ | ----------- |
|**/all**|指定 **/header**、**/bytes**、**/stats**、**/classlist** 與 **/tokens** 選項的組合。|
|**/classlist**|包括模組中定義的類別清單。|
|**/forward**|使用 forward 類別宣告。|
|**/headers**|在輸出中包含檔案標頭資訊。|
|**/item:** `class`[**::** `member`[`(sig`]]|根據提供的引數反組譯下列項目：<br /><br /> -   反組譯指定的 `class`。<br />-   反組譯 `class` 的指定 `member`。<br />-   以指定的簽章 `sig` 反組譯 `class` 的 `member`。 `sig` 的格式為：<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **注意**：在 .NET Framework 1.0 和 1.1 版中，`sig` 後面必須接著右括號：`(sig)`。 從 .NET Framework 2.0 開始，必須省略右括號：(`sig`。|
|**/noil**|隱藏 IL 組件的程式碼輸出。|
|**/stats**|包含影像中的統計資料。|
|**/typelist**|產生完整的類型清單，以便在反覆存取時保留類型順序。|
|**/unicode**|使用 Unicode 編碼輸出。|
|**/utf8**|使用 UTF-8 編碼輸出。 預設值為 ANSI。|

下列選項只對檔案或主控台輸出的 *.exe*、*.dll*、*.obj*、*.lib* 和 *.winmd* 檔案有效。

| 選項 | 說明 |
| ------ | ----------- |
|**/metadata**[=`specifier`]|顯示中繼資料，其中 `specifier` 是：<br /><br /> **MDHEADER**：顯示中繼資料的標頭資訊和大小。<br /><br /> **HEX**：使用十六進位和文字顯示資訊。<br /><br /> **CSV**：顯示記錄計數和堆積大小。<br /><br /> **UNREX**：顯示無法解析的外部符號。<br /><br /> **SCHEMA**：顯示中繼資料的標頭和結構描述資訊。<br /><br /> **RAW**：顯示原始中繼資料表。<br /><br /> **HEAPS**：顯示原始的堆積。<br /><br /> **VALIDATE**：驗證中繼資料的一致性。<br /><br /> 您可以多次指定 **/metadata**，每次使用不同的 `specifier` 值。|

下列選項只對檔案或主控台輸出的 *.lib* 檔案有效。

| 選項 | 說明 |
| ------ | ----------- |
|**/objectfile**=`filename`|顯示所指定程式庫中單一物件檔案的中繼資料。|

> [!NOTE]
> *Ildasm.exe* 的所有選項都不區分大小寫，並以前三個字母來辨識。 例如，**/quo** 相當於 **/quoteallnames**。 指定引數的選項可以接受冒號 (:) 或等號 (=) 做為選項與引數之間的分隔符號。 例如，**/output:** <檔案名稱> 相當於 **/output=** <檔案名稱>。

## <a name="remarks"></a>備註

*Ildasm.exe* 只在磁碟上的 PE 檔上作業。 它無法在安裝於全域組件快取中的檔案上作業。

*Ildasm.exe* 所產生的文字檔可以用作 IL 組譯工具 (*Ilasm.exe*) 的輸入。 這非常有用，例如在不支援所有執行階段中繼資料屬性的程式語言中編譯程式碼時。 編譯完程式碼並透過 *Ildasm.exe* 執行其輸出後，可以手動編輯產生的 IL 文字檔來新增遺漏的屬性。 然後可以透過 IL 組譯工具執行這個文字檔來產生最後的可執行檔。

> [!NOTE]
> 目前您無法將這項技術用於包含內嵌機器碼的 PE 檔 (例如，由 Visual C++ 所產生的 PE 檔)。  

您可以使用 IL 反組譯工具中的預設 GUI，檢視階層樹狀檢視中任何現有 PE 檔的中繼資料和反組譯碼。 若要使用 GUI，請在命令列鍵入 **ildasm**，但不提供 *PEfilename* 引數或任何選項。 您可以從 [檔案] 功能表巡覽至要載入 *Ildasm.exe* 中的 PE 檔。 若要儲存針對所選取 PE 顯示的中繼資料和反組譯程式碼，請選取 [檔案] 功能表中的 [傾印] 命令。 若只要儲存階層樹狀檢閱，請從 [檔案] 功能表中選取 [傾印樹狀檢視] 命令。 如需將檔案載入 *Ildasm.exe* 和解譯輸出的詳細指引，請參閱位於 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 隨附 [Samples] 資料夾中的 *Ildasm.exe* 教學課程。

如果您將包含內嵌資源的 *PEfilename* 引數提供給 *Ildasm.exe*，這個工具就會產生多個輸出檔案：包含 IL 程式碼的文字檔；每個內嵌的 Managed 資源還會各有一個使用來自中繼資料的資源名稱所產生的 .resources 檔案。 如果 Unmanaged 資源內嵌於 *PEfilename*，**/output** 選項就會使用為 IL 指定的檔案名稱來產生 .res 檔案。

> [!NOTE]
> *Ildasm.exe* 僅會顯示 *.obj* 和 *.lib* 輸入檔的中繼資料描述。 這些檔案類型的 IL 程式碼不會進行反組譯。

您可以對 .exe 或 *.dll* 檔案執行 *Ildasm.exe* 來判斷該檔案是否為 Managed。 如果檔案不是 Managed，工具便會顯示一則訊息，說明該檔案沒有有效的通用語言執行平台標頭而且無法進行反組譯。 如果檔案是 Managed，工具就會成功執行。

## <a name="version-information"></a>版本資訊

從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，*Ildasm.exe* 會藉由顯示原始二進位內容來處理無法辨認的封送處理 BLOB (二進位大型物件)。 例如，下列程式碼將示範如何顯示 C# 程式所產生的封送處理 BLOB：

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，*Ildasm.exe* 會顯示套用至介面實作的屬性，如下面 *Ildasm.exe* 輸出的摘要所示：

```
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

## <a name="examples"></a>範例

下列命令會讓 PE 檔 `MyHello.exe` 的中繼資料和反組譯程式碼顯示於 *Ildasm.exe* 的預設 GUI 中。

```console
ildasm myHello.exe
```

下列命令會反組譯 `MyFile.exe` 檔案，並將產生的 IL 組譯工具文字儲存到 *MyFile.il* 檔案中。

```console
ildasm MyFile.exe /output:MyFile.il
```

下列命令會反組譯 `MyFile.exe` 檔案，並在主控台視窗中顯示產生的 IL 組譯工具文字。

```console
ildasm MyFile.exe /text
```

如果檔案 `MyApp.exe` 包含內嵌的受控和非受控資源，則下列命令會產生四個檔案：*MyApp.il*、*MyApp.res*、*Icons.resources* 和 *Message.resources*：

```console
ildasm MyApp.exe /output:MyApp.il
```

下列命令會反組譯 `MyFile.exe` 中 `MyClass` 類別內的 `MyMethod` 方法，並且在主控台視窗中顯示輸出。

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

在上述範例中，可能有數個名為 `MyMethod` 但具有不同簽章的方法。 下列命令會反組譯傳回型別為 **void** 以及參數類型為 **int32** 和 **string** 的執行個體方法 `MyMethod`。

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> 在 .NET Framework 1.0 和 1.1 版中，方法名稱後的左括號必須與簽章後的右括號保持對稱：`MyMethod(instance void(int32))`。 從 .NET Framework 2.0 開始，必須省略右括號：`MyMethod(instance void(int32)`。

若要擷取 `static` 方法 (在 Visual Basic 中為 `Shared` 方法)，請省略關鍵字 `instance`。 不是 `int32` 和 `string` 等基本類型 (Primitive Type) 的類別類型，都必須包含命名空間，而且前面必須加上關鍵字 `class`。 外部類型的前面必須加上以方括號括住的程式庫名稱。 下列命令會反組譯名為 `MyMethod` 的靜態方法，該靜態方法具有一個 <xref:System.AppDomain> 類型的參數，而且傳回類型為 <xref:System.AppDomain>。

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

巢狀類型的前面必須加上它的包含類別，並以正斜線分隔。 例如，如果 `MyNamespace.MyClass` 類別包含名為 `NestedClass` 的巢狀類別，則該巢狀類別的識別方式如下：`class MyNamespace.MyClass/NestedClass`。

## <a name="see-also"></a>另請參閱

- [工具](../../../docs/framework/tools/index.md)
- [Ilasm.exe (IL 組譯工具)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)
- [Managed 執行程序](../../../docs/standard/managed-execution-process.md)
- [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
