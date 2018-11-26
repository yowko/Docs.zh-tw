---
title: Windows 系統上的檔案路徑格式
ms.date: 06/28/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b79ff1991f1d9b803b0c35b4ae9565f70de0b56
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296824"
---
# <a name="file-path-formats-on-windows-systems"></a>Windows 系統上的檔案路徑格式

<xref:System.IO> 命名空間中許多類型的成員都包含 `path` 參數，這可讓您指定檔案系統資源的絕對或相對路徑。 接著這個路徑會傳遞給 [Windows 檔案系統 API](https://msdn.microsoft.com/library/windows/desktop/aa364407(v=vs.85).aspx)。 本主題討論您可以在 Windows 系統上使用的檔案路徑格式。

## <a name="traditional-dos-paths"></a>傳統 DOS 路徑

標準 DOS 路徑可以包含三個元件：

- 磁碟區或磁碟機代號，後面接著磁碟區分隔符號 (`:`)。
- 目錄名稱。 [目錄分隔符號字元](<xref:System.IO.Path.DirectorySeparatorChar>)會分隔巢狀目錄階層內的子目錄。
- 選擇性的檔名。 [目錄分隔符號字元](<xref:System.IO.Path.DirectorySeparatorChar>)會分隔檔案路徑和檔案名稱。

如果三個元件全都存在，則是絕對路徑。 如果未指定任何磁碟區或磁碟機代號，且目錄名稱開頭為[目錄分隔符號字元](<xref:System.IO.Path.DirectorySeparatorChar>)，則路徑是相對於目前磁碟機的根目錄。 否則，路徑是相對於目前的目錄。 下表顯示一些可能的目錄和檔案路徑。

|路徑  |描述  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | 從磁碟機 C: 根目錄開始的絕對檔案路徑 |
| `\Program Files\Custom Utilities\StringFinder.exe` | 從目前磁碟機根目錄開始的絕對路徑。 |
| `2018\January.xlsx` | 到目前目錄之子目錄中檔案的相對路徑。 |
| `..\Publications\TravelBrochure.pdf` | 到目前目錄之同級目錄中檔案的相對路徑。 |
| `C:\Projects\apilibrary\apilibrary.sln` | 從磁碟機 C: 根目錄開始的絕對檔案路徑 |
| `C:Projects\apilibrary\apilibrary.sln` | 從磁碟機 C: 目前目錄開始的相對路徑。 |

> [!IMPORTANT]
> 請注意最後兩個路徑之間的差異。 同時指定選用的磁碟區規範 (在兩個案例中都是 C:)，但第一個的開頭是指定磁碟區的根目錄，而第二個則否。 因此，第一個是從磁碟機 C: 根目錄開始的絕對路徑，而第二個則是從磁碟機 C: 目前目錄開始的相對路徑。 當想要第一種格式時使用第二種格式，是在牽涉到 Windows 檔案路徑時常見的錯誤來源。

您可以呼叫 <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> 方法來判斷檔案路徑是否完整 (也就是路徑獨立於目前的目錄，目前目錄變更時它不會變更)。 請注意，這類路徑可以包含相對目錄區段 (`.` 和 `..`)，而且如果解析的路徑永遠指向相同位置便仍然完整。

下例會說明絕對和相對路徑之間的差異。 它假設目錄 D:\FY2018\ 存在，且在執行此範例之前，您還沒有從命令提示字元設定 D:\ 的任何目前目錄。

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

## <a name="unc-paths"></a>UNC 路徑

通用命名慣例 (UNC) 路徑，用來存取網路資源，具有下列格式：

- 伺服器或主機名稱，前面加上 \\\\。 伺服器名稱可以是 NetBIOS 電腦名稱或 IP/FQDN 位址 (支援 IPv4 以及 v6)。
- 共用名稱，它藉由 \\ 與主機名稱分隔。 伺服器和共用名稱會共同組成磁碟區。
- 目錄名稱。 [目錄分隔符號字元](<xref:System.IO.Path.DirectorySeparatorChar>)會分隔巢狀目錄階層內的子目錄。
- 選擇性的檔名。 [目錄分隔符號字元](<xref:System.IO.Path.DirectorySeparatorChar>)會分隔檔案路徑和檔案名稱。

以下是 UNC 路徑的一些範例：

|路徑  |描述  |
| -- | -- |
| `\\system07\C$\` | `system07` 上磁碟機 C: 的根目錄。 |
| `\\Server2\Share\Test\Foo.txt` | \\\\Server2\\Share 磁碟區 Test 目錄中的 Foo.txt 檔案。|

UNC 路徑必須一律完整。 它們可以包含相對目錄區段 (`.` 和 `..`)，但這些必須是完整路徑的一部分。 您只能藉由將 UNC 路徑對應至磁碟機代號來使用相對路徑。

## <a name="dos-device-paths"></a>DOS 裝置路徑

Windows 作業系統有指向包括檔案在內所有資源的　統一物件模型。 這些物件路徑可從 [主控台] 視窗存取，並已透過舊版 DOS 和 UNC 路徑對應到的符號連結特殊資料夾，公開至 Win32 圖層。 這個特殊資料夾是透過 DOS 裝置路徑語法來存取，這是其中一個：

`\\.\C:\Test\Foo.txt`  
`\\?\C:\Test\Foo.txt`

> [!NOTE]
> 從 .NET Core 1.1 和 .NET Framework 4.6.2 開始，在 Windows 上執行的 .NET 實作會支援 DOS 裝置路徑語法。

DOS 裝置路徑由以下元件組成：

- 裝置路徑規範 (`\\.\` 或 `\\?\`)，這會將路徑識別為 DOS 裝置路徑。

   > [!NOTE]
   > `\\?\` 在所有版本的 .NET Core 和 4.6.2 版開始的 .NET Framework 中受到支援。
   
- 「真實」裝置物件的符號連結 (在此案例中為 C:)。

   裝置路徑規範識別磁碟區或磁碟機之後，DOS 裝置路徑的第一個區段。 (例如，`\\?\C:\` 和 `\\.\BootPartition\`。)

   對於呼叫的 UNC 有一個特定連結，不用多說，就是 `UNC`。 例如: 

  `\\.\UNC\Server\Share\Test\Foo.txt`  
  `\\?\UNC\Server\Share\Test\Foo.txt`

    針對裝置 UNC，「伺服器/共用」部分會形成磁碟區。 例如，在 `\\?\server1\e:\utilities\\filecomparer\`，「伺服器/共用」部分是 server1\utilities。 這一點在呼叫具有相對目錄區段的方法 (例如 <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType>) 時很重要；無法瀏覽過磁碟區。 

根據定義，DOS 裝置路徑是完整的。 不允許相對目錄區段 (`.` 和 `..`)。 目前目錄絕對不會進入其使用方式。

## <a name="example-ways-to-refer-to-the-same-file"></a>範例：如何參考相同的檔案

下列範例說明一些您可以用來在 <xref:System.IO> 命名空間使用 API 時參考檔案的方法。 範例會具現化 <xref:System.IO.FileInfo> 物件，並使用其 <xref:System.IO.FileInfo.Name> 和 <xref:System.IO.FileInfo.Length> 屬性，以顯示檔案名稱和檔案的長度。

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>路徑正規化

幾乎傳遞給 Windows API 的所有路徑都會正規化。 在正規化期間，Windows 會執行下列步驟：

- 識別路徑。
- 將目前目錄套用到部份限定 (相對) 路徑。
- 規範化元件和目錄分隔符號。
- 評估相對目錄元件 (`.` 表示目前目錄，`..` 表示父目錄)。
- 修剪特定字元。

這個正規化會隱含地發生，但您可以明確地呼叫 <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> 方法來執行，這個方法會包裝對 [GetFullPathName() 函式](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)的呼叫。 您也可以直接使用 P/Invoke 呼叫 Windows [GetFullPathName() 函式](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)。

### <a name="identifying-the-path"></a>識別路徑

路徑正規化的第一步就是識別路徑的類型。 路徑會落在一些分類的其中之一：

- 它們是裝置路徑，亦即它們開頭為兩個分隔符號和一個問號或句點 (`\\?` 或 `\\.`)。
- 它們是 UNC 路徑，亦即它們開頭為兩個分隔符號，且沒有問號或句點。 
- 它們是完整的 DOS 路徑，亦即它們開頭為磁碟機代號、磁碟區分隔符號和元件分隔符號 (`C:\`)。
- 它們指定舊版裝置 (`CON`、`LPT1`)。
- 它們相對於目前磁碟機的根目錄，亦即它們開頭單一元件分隔符號 (`\`)。
- 它們相對於指定磁碟機的目前目錄，亦即它們開頭為磁碟機代號、磁碟區分隔符號，且沒有元件分隔符號 (`C:`)。
- 它們相對於目前目錄，亦即它們開頭為其他任何字元 (`temp\testfile.txt`)。

路徑的類型會決定是否要以某種方式套用目前目錄。 它也會判斷路徑的「根」是什麼。

### <a name="handling-legacy-devices"></a>處理舊版裝置

如果路徑是舊版 DOS 裝置，例如 `CON`、`COM1` 或 `LPT1`，會在它前面加上 `\\.\` 轉換為裝置路徑然後傳回。 

開頭為舊版裝置名稱的路徑，一律會被 <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> 方法解譯成舊版裝置。 例如，`CON.TXT` 的 DOS 裝置路徑是 `\\.\CON`，而 `COM1.TXT\file1.txt` 的 DOS 裝置路徑是 `\\.\COM1`。

### <a name="applying-the-current-directory"></a>套用目前目錄

如果路徑不是完整格式，Windows 會套用目前目錄給它。 UNC 和裝置路徑沒有套用目前目錄。 具有分隔符號 C:\\ 的完整磁碟機也不會套用。

如果路徑開頭為單一元件分隔符號，則會套用目前目錄的磁碟機。 例如，如果檔案路徑是 `\utilities`，而目前目錄是 `C:\temp\`，則正規化會產生 `C:\utilities`。

如果路徑開頭為磁碟機代號、磁碟區分隔符號且沒有元件分隔符號，則會套用從命令殼層設定的指定磁碟機最後一個目前目錄。 如果未設定最後一個目前目錄，則會單獨套用磁碟機。 例如，如果檔案路徑是 `D:sources`目前目錄是 `C:\Documents\`，且磁碟機 D: 上的最後一個目前目錄是 `D:\sources\`，則結果是 `D:\sources\sources`。 這些「磁碟機相對」路徑是常見的程式和指令碼邏輯錯誤來源。 假設開頭為代號與冒號的路徑不是相對路徑，這顯然不正確。

如果路徑開頭為分隔符號以外的項目，則會套用目前磁碟機和目前目錄。 例如，如果路徑是 `filecompare`，而目前目錄是 `C:\utilities\`，則結果是 `C:\utilities\filecompare\`。

> [!IMPORTANT]
> 相對路徑在多執行緒應用程式 (也就是大部分應用程式) 中是危險的，因為目前目錄是以每個處理序為基準的一項設定。 任何執行緒都可以隨時變更目前目錄。 從 .NET Core 2.1 開始，您可以呼叫 <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> 方法，從相對路徑以及您想要解析針對的基底路徑 (目前的目錄)，取得絕對路徑。 

### <a name="canonicalizing-separators"></a>規範化分隔符號

所有正斜線 (`/`) 會轉換成標準的 Windows 分隔符號，也就是反斜線 (`\`)。 如果它們存在，跟隨在前兩個斜線後面的一系列斜線，會摺疊成單一斜線。

### <a name="evaluating-relative-components"></a>評估相對元件

處理路徑時，會評估由單一或雙句點 (`.` 或 `..`) 所組成的任何元件或區段： 

- 若為單一句點，會移除目前的區段，因為它是指目前目錄。

- 若為雙句點，會移除目前的區段和父區段，因為雙句點是指父目錄。

   只有在父目錄不超過路徑的根目錄時，才會移除父目錄。 路徑的根目錄取決於路徑的類型。 對於 DOS 路徑是磁碟機 (`C:\`)、對於 UNC 是伺服器/共用 (`\\Server\Share`)，以及對於裝置路徑則是裝置路徑前置詞 (`\\?\` 或 `\\.\`)。

### <a name="trimming-characters"></a>修剪字元

在稍早移除分隔符號和相對區段時，正規化期間也會額外移除一些字元：

- 如果區段結尾為單一句點，會移除該句點。 (單句點或雙句點的區段在上一個步驟中正規化。 三個以上句點的區段不會正規化，且實際上是有效的檔案/目錄名稱。)

- 如果路徑結尾不是分隔符號，所有尾端句號和空格 (U+0020) 都會移除。 如果最後一個區段只是單句點或雙句點，它會屬於上述相對元件規則。 

   此規則表示您可以建立具有尾端空格的目錄名稱，方法是在空格之後新增尾端分隔符號。  

   > [!IMPORTANT]
   > 您應該**絕不**建立具有尾端空格的目錄或檔案名稱。 尾端空格可能會導致難以存取目錄或是不可能存取目錄，而應用程式在嘗試處理名稱包含尾端空格的目錄或檔案時，通常會失敗。

## <a name="skipping-normalization"></a>略過正規化

一般而言，任何傳遞給 Windows API 的路徑 (實際上) 會傳遞給 [GetFullPathName 函式](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)並正規化。 有一個重要的例外狀況：開頭為問號而非句號的裝置路徑。 除非路徑開頭完全為 `\\?\`(請注意我們使用了標準的反斜線)，否則它會正規化。

為何會想要略過正規化？ 有三個主要的原因：

1. 存取通常無法使用，但是合法的路徑。 例如，稱為 `hidden.` 的檔案或目錄便無法以任何其他方式存取。 

1. 如果已經正規化，藉由略過正規化以改善效能。

1. (僅限 .NET Framework) 略過路徑長度的 `MAX_PATH` 檢查，以允許超過 259 個字元的路徑。 大部分的 API 都允許這點，但有些例外狀況。

> [!NOTE]
> .NET Core 會隱含地處理長路徑，而不會執行 `MAX_PATH` 檢查。 `MAX_PATH` 檢查只適用於 .NET Framework。

略過正規化和最大路徑檢查是兩個裝置路徑語法之間唯一的差異，它們在其他方面都一樣。 略過正規化時請小心，因為您可能會很容易就建立令「正常」應用程式難以處理的路徑。

開頭為 `\\?\` 的路徑，在您明確地將其傳遞給 [GetFullPathName 函式](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)時，仍會正規化。

請注意，您可以將多於 `MAX_PATH` 個字元的路徑傳遞給 [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) 而不需要 `\\?\`。 它支援最長可達 Windows 可處理字串大小上限的任意長度路徑。

## <a name="case-and-the-windows-file-system"></a>大小寫與 Windows 檔案系統

對於 Windows 檔案系統的特色，非 Windows 使用者和開發人員感到困惑的一點就是路徑和目錄名稱不區分大小寫。 也就是說，目錄和檔案名稱會反映它們建立時所使用的字串大小寫。 例如，方法呼叫

```csharp
Directory.Create("TeStDiReCtOrY");
```
會建立名為 TeStDiReCtOrY 的目錄。 如果您重新命名目錄或檔案，以變更其大小寫，目錄或檔案名稱會反映將它重新命名時所使用字串的大小寫。 例如，下列程式碼將一個名為 test.txt 的檔案重新命名為 Test.txt：

```csharp
using System;
using System.IO;

class Example
{
   public static void Main()
   {
      var fi = new FileInfo(@".\test.txt");
      fi.MoveTo(@".\Test.txt");
   }
}
``` 
```vb
Imports System.IO

Module Example
   Public Sub Main()
      Dim fi As New FileInfo(".\test.txt")
      fi.MoveTo(".\Test.txt")
   End Sub
End Module
```

不過，目錄和檔案名稱比較不區分大小寫。 如果您搜尋名為 "test.txt" 的檔案，.NET 檔案系統 API 在比較時會忽略大小寫。 Test.txt、TEST.TXT、test.TXT 和大寫和小寫字母的任何其他組合都會符合 "test.txt"。
