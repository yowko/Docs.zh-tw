---
title: 使用 Parallel.ForEach 寫入一個簡單的平行程式
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d54f06c1fc774a2e73b3b99a7d5bb24dd8baf3f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835268"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>HOW TO：撰寫簡單的 Parallel.ForEach 迴圈

此範例示範如何使用 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 迴圈來透過 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 資料來源啟用資料平行處理原則。

> [!NOTE]
> 本文件使用 Lambda 運算式來定義 PLINQ 中的委派。 如果您不熟悉 C# 或 Visual Basic 中的 Lambda 運算式，請參閱 [PLINQ 及 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。

## <a name="example"></a>範例

此範例會假設您在 C:\Users\Public\Pictures\Sample Pictures 資料夾中擁有數個 .jpg 檔案，且建立名為 *Modified* 的新子資料夾。 當您執行範例時，其會旋轉在 *Sample Pictures* 中的各 .jpg 影像，並將其儲存至 *Modified*。 如有必要，您可以修改這兩個路徑。

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 迴圈的運作方式類似 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 迴圈。 迴圈會根據系統環境分割來源集合，及對多個執行緒上的作業進行排程。 系統上的處理器愈多，平行方法的執行速度愈快。 對於某些來源集合，循序迴圈的執行速度可能更快，這取決於來源的大小和迴圈執行的作業種類。 如需效能的詳細資訊，請參閱[資料和工作平行](potential-pitfalls-in-data-and-task-parallelism.md)處理原則中的可能錯誤。

如需平行迴圈的詳細資訊，請參閱[如何：撰寫簡單的 Parallel.For 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)。

若要將 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>使用於非泛型集合 ，可使用 <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> 擴充方法將集合轉換成泛型集合，如下列範例所示：

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

您也可以使用平行 LINQ (PLINQ) 來平行處理 <xref:System.Collections.Generic.IEnumerable%601> 資料來源。 PLINQ 可讓您使用宣告式查詢語法來表示迴圈行為。 如需詳細資訊，請參閱 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)。

## <a name="compile-and-run-the-code"></a>編譯並執行程式碼

您可將程式碼編譯為 .NET Framework 的主控台應用程式，或 .NET Core 的主控台應用程式。

在 Visual Studio 中，有 Windows Desktop 及 .NET Core 的 Visual Basic 及 C# 主控台應用程式範本。

從命令列中，您可使用 .NET Core 及其 CLI 工具 (例如 `dotnet new console` 或 `dotnet new console -lang vb`)，或者可建立檔案，然後使用 .NET Framework 應用程式的命令列編譯器。

對於 .NET Core 專案，您必須參考 **System.Drawing.Common** NuGet 套件。 在 Visual Studio 中，使用 NuGet 套件管理員來安裝套件。 或者，您可將參考新增至 \*.csproj 或 \*.vbproj 檔案中的套件：
 
```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

若要從命令列執行 .NET Core 主控台應用程式，請從包含您應用程式的資料夾中使用 `dotnet run`。

若要從 Visual Studio 執行您的主控台應用程式，請按 **F5**。

## <a name="see-also"></a>另請參閱

- [資料平行處理原則](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [平行程式設計](../../../docs/standard/parallel-programming/index.md)
- [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
