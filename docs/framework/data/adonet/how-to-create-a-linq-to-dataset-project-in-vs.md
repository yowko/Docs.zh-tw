---
title: 建立 LINQ to DataSet 專案在 Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 22763d3b9581d09d7bdda0c09480f8d36bb8e2ec
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154030"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>HOW TO：建立 LINQ to DataSet 專案在 Visual Studio

LINQ 專案的不同類型需要特定的組件參考和匯入的命名空間 (Visual Basic) 或[使用](../../../csharp/language-reference/keywords/using-directive.md)指示詞 (C#)。 LINQ 的最低需求是參考*System.Core.dll*並`using`指示詞<xref:System.Linq>。

如果您在 Visual Studio 2017 中建立的新 C# 主控台應用程式專案預設會提供這些需求。 如果您要從舊版的 Visual Studio 升級專案，您可能必須以手動方式提供這些 LINQ 相關參考。

LINQ to DataSet 需要兩個額外參考*System.Data.dll*並*System.Data.DataSetExtensions.dll*。

> [!NOTE]
> 如果您要從命令提示字元建置，就必須手動參考中的 LINQ 相關 Dll *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*。

## <a name="to-enable-linq-to-dataset-functionality"></a>若要啟用 LINQ to DataSet 功能

請遵循下列步驟來啟用 LINQ to DataSet 功能，在現有的專案。

1. 將參考加入至**System.Core**， **System.Data**，並**System.Data.DataSetExtensions**。

   在 [**方案總管] 中**，以滑鼠右鍵按一下**參考**節點，然後選取**加入參考**。 在 **參考管理員**對話方塊中，選取**System.Core**， **System.Data**，以及**System.Data.DataSetExtensions**。 選取 [確定]。

1. 新增[使用](../../../csharp/language-reference/keywords/using-directive.md)指示詞 (或[Imports 陳述式](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)Visual Basic 中) 的**System.Data**並**System.Linq**。

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. （選擇性） 加入`using`指示詞 (或`Imports`陳述式) 的**System.Data.Common**或是**System.Data.SqlClient**，取決於連接到資料庫的方式。

## <a name="see-also"></a>另請參閱

- [開始使用 LINQ to DataSet](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
