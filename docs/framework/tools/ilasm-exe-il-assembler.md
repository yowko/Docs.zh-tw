---
title: Ilasm.exe (IL 組譯工具)
description: 開始使用 Ilasm.exe，也就是 IL 組合器。 此工具會從中繼語言（IL）產生可移植的可執行檔（PE）。
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: 1a85b3bf9509ffba6c2331d14196a6bef2bfa080
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166982"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (IL 組譯工具)

IL Assembler 可從中繼語言 (IL) 中產生可攜式執行檔 (PE) （如需 IL 的詳細資訊，請參閱[Managed 執行](../../standard/managed-execution-process.md)程式）。您可以執行產生的可執行檔（其中包含 IL 和必要的中繼資料），以判斷 IL 是否如預期般執行。

此工具會自動與 Visual Studio 一起安裝。 若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。

在命令提示字元中，請輸入下列項目：

## <a name="syntax"></a>語法

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a>參數

| 引數 | 描述 |
| -------- | ----------- |
|`filename`|.il 原始程式檔的名稱。 這個檔案由中繼資料宣告指示詞和符號 IL 指令組成。 可以提供多個來源檔案引數，以產生具有*Ilasm.exe*的單一 PE 檔案。 **注意：** 請確定 il 原始程式檔中的最後一行程式碼有尾端空白字元或行結尾字元。|

| 選項 | 描述 |
| ------ | ----------- |
|**/32bitpreferred**|建立一個 32 位元慣用的映像 (PE32)。|
|**/alignment：**`integer`|將 FileAlignment 設定為 NT Optional 標頭中 `integer` 指定的值。 如果在檔案中指定了 .alignment IL 指示詞，這個選項會覆寫它。|
|**/appcontainer**|產生在 Windows 應用程式容器中執行的 *.dll*或 *.exe*檔案，做為輸出。|
|**/arm**|指定進階 RISC 機器 (ARM) 為目標處理器。<br /><br /> 如果沒有指定映像位元，則預設為 **/32bitpreferred**。|
|**/base：**`integer`|將 ImageBase 設定為 NT Optional 標頭中 `integer` 指定的值。 如果在檔案中指定了 .imagebase IL 指示詞，這個選項會覆寫它。|
|**/clock**|對指定的 .il 原始程式檔以毫秒為單位測量並且報告下列編譯時間：<br /><br /> **總共執行**：執行所有緊接在後之特定作業所花費的總時間。<br /><br /> **啟動**：載入和開啟檔案。<br /><br /> **發出 MD**：發出中繼資料。<br /><br /> **定義參考解析**：解析檔案中的定義參考。<br /><br /> **產生 CEE 檔案**：在記憶體中產生檔案映像。<br /><br /> **撰寫 PE 檔案**：撰寫 PE 檔案的映像。|
|**/debug**[:**IMPL**&#124;**OPT**]|包含偵錯資訊 (區域變數和引數名稱以及行號)。 建立 PDB 檔案。<br /><br /> 不帶其他值的 **/debug** 會停用 JIT 最佳化，並使用 PDB 檔案的序列點。<br /><br /> **IMPL** 會停用 JIT 最佳化，並使用隱含序列點。<br /><br /> **OPT** 會啟用 JIT 最佳化，並使用隱含序列點。|
|**/dll**|產生 *.dll*檔案做為輸出。|
|**/enc：**`file`|從指定的原始程式檔建立編輯後繼續差異。<br /><br /> 這個引數僅供教育使用，而不支援商業用途。|
|**/exe**|產生可執行檔做為輸出。 這是預設值。|
|**/flags：**`integer`|將 ImageFlags 設定為通用語言執行平台標頭中 `integer` 指定的值。 如果在檔案中指定了 .corflags IL 指示詞，這個選項會覆寫它。 如需 *integer*有效值的清單，請參閱 CorHdr.h，COMIMAGE_FLAGS。|
|**/fold**|將相同的方法主體摺疊為一。|
|/**highentropyva**|產生一個輸出可執行檔，此檔支援高熵位址空間隨機載入 (ASLR)。 (預設為 **/appcontainer**)。|
|**/include：**`includePath`|設定路徑以搜尋與 `#include`一起包含的檔案。|
|**/itanium**|將 Intel Itanium 指定為目標處理器。<br /><br /> 如果沒有指定映像位元，則預設為 **/pe64**。|
|**/key：**`keyFile`|使用包含在 `keyFile` 的私密金鑰來編譯含有強式簽章的 `filename`。|
|**/key** @`keySource`|使用產生於 `keySource` 的私密金鑰來編譯含有強式簽章的 `filename`。|
|**/listing**|產生標準輸出上的清單檔。 如果省略這個選項，將不會產生任何清單檔。<br /><br /> .NET Framework 2.0 (含) 以後不支援此參數。|
|**/mdv：**`versionString`|設定中繼資料版本字串。|
|**/msv：** `major` 。`minor`|設定中繼資料流版本，其中 `major` 和 `minor` 是整數。|
|**/noautoinherit**|沒有指定基底類別時，停用 <xref:System.Object> 的預設繼承。|
|**/nocorstub**|隱藏 CORExeMain 虛設常式 (Stub) 的產生。|
|**/nologo**|隱藏 Microsoft 程式啟始資訊顯示。|
|**/output：**`file.ext`|指定輸出檔的名稱和副檔名。 依預設值，輸出檔的名稱和第一個原始程式檔的名稱相同。 預設副檔名為 *.exe*。 如果您指定 **/dll**選項，預設副檔名會是 *.dll*。 **注意：** 指定 **/output**:myfile.dll 不會設定 **/dll**選項。 如果您未指定 **/dll**，結果會是名為*myfile.dll*的可執行檔。|
|**/optimize**|將長指令最佳化為短指令。 例如， `br` 變成 `br.s`。|
|**/pe64**|建立 64 位元的映像 (PE32+)。<br /><br /> 如果沒有指定目標處理器，則預設為 `/itanium`。|
|**/pdb**|在不啟用偵錯資訊追蹤的情況下建立 PDB 檔案。|
|**/quiet**|指定安靜模式；不報告組譯碼 (Assembly) 程序。|
|**/resource：**`file.res`|以 .res 格式將指定的資源檔包含在 \* 產生的 *.exe*或 *.dll*檔案中。 使用 **/resource** 選項只能指定一個 .res 檔。|
|**/ssver：** `int` 。`int`|設定在 NT 選擇標題上的子系統版本號碼。 對於 **/appcontainer** 和 **/arm** 的最小版本號碼為 6.02。|
|**/stack：**`stackSize`|將 NT 選擇性標頭中的 SizeOfStackReserve 值設定為 `stackSize`。|
|**/stripreloc**|指定不需要基底重新配置。|
|**/subsystem：**`integer`|將子系統設定為 NT Optional 標頭中 `integer` 指定的值。 如果在檔案中指定了 .subsystem IL 指示詞，這個命令會覆寫它。 如需 `integer`有效值的清單，請參閱 winnt.h，IMAGE_SUBSYSTEM。|
|**/x64**|將 64 位元的 AMD 處理器指定為目標處理器。<br /><br /> 如果沒有指定映像位元，則預設為 **/pe64**。|
|**/?**|顯示工具的命令語法和選項。|

> [!NOTE]
> *Ilasm.exe*的所有選項都不區分大小寫，且前三個字母都能辨識。 例如， **/lis**相當於 **/listing** ，而 **/res**： myresfile.res 相當於 **/resource**： myresfile.res. .res。指定引數的選項會接受冒號（:)或等號（=）做為選項和引數之間的分隔符號。 例如， **/output**：*file. ext*相當於 **/output** = *副檔名*。

## <a name="remarks"></a>備註

IL 組譯工具可協助工具廠商設計及實作 IL 產生器。 使用*Ilasm.exe*，工具和編譯器開發人員可以專注于 il 和中繼資料的產生，而不需要擔心以 PE 檔案格式發出 il。

類似于以執行時間為目標的其他編譯器，例如 c # 和 Visual Basic， *Ilasm.exe*不會產生中繼目的檔，而且不需要連結階段來形成 PE 檔。

IL 組譯工具可以表示所有現有的中繼資料和以執行階段為目標之程式語言的 IL 功能。 這可讓以任何程式設計語言撰寫的 managed 程式碼，在 IL 組合器中適當地表示，並使用*Ilasm.exe*進行編譯。

> [!NOTE]
> 如果 .il 原始程式檔中程式碼的最後一行沒有尾端空白字元或行結尾字元，編譯就可能會失敗。

您可以使用*Ilasm.exe*搭配其附屬工具， [*Ildasm.exe*](ildasm-exe-il-disassembler.md)。 *Ildasm.exe*採用包含 IL 程式碼的 PE 檔案，並建立適合做為*Ilasm.exe*輸入的文字檔。 這非常有用，例如在不支援所有執行階段中繼資料屬性的程式語言中編譯程式碼時。 在編譯器代碼並透過*Ildasm.exe*執行輸出之後，可以手動編輯產生的 IL 文字檔來加入遺漏的屬性。 接著，您可以透過*Ilasm.exe*執行這個文字檔，以產生最終的可執行檔。

您也可以使用這項技術來由不同編譯器所原始產生的數個 PE 檔中產生單一 PE 檔。

> [!NOTE]
> 目前您無法將這項技術用於包含內嵌機器碼的 PE 檔 (例如，由 Visual C++ 所產生的 PE 檔)。

為了讓*Ildasm.exe*和*Ilasm.exe*的結合使用盡可能精確，根據預設，組合器不會將簡短編碼取代為您可能已在 IL 來源（或由另一個編譯器發出的）中寫入的長時間。 使用 **/optimize** 選項在可能的情況下替代短編碼方式。

> [!NOTE]
> *Ildasm.exe*只會對磁片上的檔案進行操作。 它無法在安裝於全域組件快取中的檔案上作業。

如需 IL 文法的詳細資訊，請參閱 Windows SDK 中的 asmparse.grammar 檔案。

## <a name="version-information"></a>版本資訊

從 .NET Framework 4.5 開始，您可以使用類似下列的程式碼來附加自訂屬性至介面實作：

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

從 .NET Framework 4.5 開始，您可以指定選擇性封送處理 BLOB (二進位大型物件) 使用其未經處理的二進位表示，如下列程式碼所示：

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

如需 IL 文法的詳細資訊，請參閱 Windows SDK 中的 asmparse.grammar 檔案。

## <a name="examples"></a>範例

下列命令會組譯 IL 檔 *myTestFile.il*，並產生可執行檔 *myTestFile.exe*。

```console
ilasm myTestFile
```

下列命令會組譯 IL 檔 *myTestFile.il*，並產生 *.dll*檔案 *myTestFile.dll*。

```console
ilasm myTestFile /dll
```

下列命令會組譯 IL 檔 *myTestFile.il*，並產生 *.dll*檔案 *myNewTestFile.dll*。

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

下列程式碼範例會顯示極為簡單的應用程式，將 "Hello World!" 顯示 。 您可以編譯此程式碼，然後使用[*Ildasm.exe*](ildasm-exe-il-disassembler.md)工具來產生 IL 檔案。

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

下列 IL 程式碼範例會對應至之前的 C# 程式碼範例。 您可以使用 IL 組譯工具，將這個程式碼編譯為組件。 IL 和 C# 這兩個程式碼範例都將 "Hello World!" 顯示 。

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a>另請參閱

- [工具](index.md)
- [*Ildasm.exe* （IL 解譯器）](ildasm-exe-il-disassembler.md)
- [Managed 執行進程](../../standard/managed-execution-process.md)
- [命令提示字元](developer-command-prompt-for-vs.md)
