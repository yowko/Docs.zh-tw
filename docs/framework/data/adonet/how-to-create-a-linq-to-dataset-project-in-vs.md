---
title: 在 Visual Studio 中建立 LINQ to DataSet 專案
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 8b905c65575c3c567459d843b2a5d1606bc63228
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783772"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>HOW TO：在 Visual Studio 中建立 LINQ to DataSet 專案

不同類型的 LINQ 專案需要特定的元件參考和匯入的命名空間（  Visual Basic）或C#[使用](../../../csharp/language-reference/keywords/using-directive.md)指示詞（）。 LINQ 的最低需求是的*system.object*參考和的`using` <xref:System.Linq>指示詞。

如果您在 Visual Studio 2017 中建立新C#的主控台應用程式專案，則預設會提供這些需求。 如果您要從舊版的 Visual Studio 升級專案，您可能必須手動提供這些 LINQ 相關的參考。

LINQ to DataSet 需要*system.data.datasetextensions.dll*的兩個額外參考 *，才能進行*。

> [!NOTE]
> 如果您是從命令提示字元建立，則必須在 *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*中手動參考 LINQ 相關的 dll。

## <a name="to-enable-linq-to-dataset-functionality"></a>若要啟用 LINQ to DataSet 功能

請遵循下列步驟，在現有的專案中啟用 LINQ to DataSet 功能。

1. 將參考新增至 System.data.datasetextensions.dll.**核心**、 **system. data**和**system.web**。

   在**方案總管**中，以滑鼠右鍵按一下 [**參考**] 節點，然後選取 [**新增參考**]。 在 [**參考管理員**] 對話方塊中，**選取 [** System.string]、[ **system.web**] 和 [ **system.data.datasetextensions.dll**]。 選取 [確定]。

1. 為**system.web**和 system.string 新增[using](../../../csharp/language-reference/keywords/using-directive.md)指示詞（或匯入 Visual Basic 中的[語句](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) **）。**

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. （選擇性）針對`using` [ **SqlClient**] `Imports`加入指示詞（或語句），視您連接到資料庫的方式而**定。**

## <a name="see-also"></a>另請參閱

- [開始使用 LINQ to DataSet](getting-started-linq-to-dataset.md)
