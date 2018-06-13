---
title: 如何：在 Visual Studio 中建立 LINQ to DataSet 專案
ms.date: 03/30/2017
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 094d766146fe55a865713a4672a2bee6a838ff55
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758863"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>如何：在 Visual Studio 中建立 LINQ to DataSet 專案
不同的 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 專案類型需要特定匯入的命名空間 (Namespace) (Visual Basic) 或 `using` 指示詞 (C#) 和參考。 最小需求是 System.Core.dll 的參考和 `using` 的 <xref:System.Linq> 指示詞。 根據預設，如果您建立新的 [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] 專案，系統就會提供這些項目。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 也需要 System.Data.dll 和 System.Data.DataSetExtensions.dll 的參考以及 `Imports` (Visual Basic) 或 `using` (C#) 指示詞。  
  
 如果您要從舊版 Visual Studio 升級專案，可能必須手動提供這些 LINQ 相關的參考。 此外，您可能也必須手動將專案設定為以 .NET Framework 3.5 版為目標。  
  
> [!NOTE]
>  如果您要從命令提示字元建置，您必須手動參考中的 LINQ 相關 Dll `drive` **:** \program Assemblies\Microsoft\Framework\v3.5。  
  
### <a name="to-target-the-net-framework-35"></a>以 .NET Framework 3.5 為目標  
  
1.  在 [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] 中，建立新的 Visual Basic 或 C# 專案。 或者，您也可以開啟在 Visual Studio 2005 中建立的 Visual Basic 或 C# 專案，然後遵循提示，將它轉換成 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 專案。  
  
2.  C# 專案，請按一下**專案**功能表，然後再按一下**屬性**。  
  
    1.  在**應用程式**屬性頁上，選取.NET Framework 3.5 中**目標 Framework**下拉式清單。  
  
3.  Visual Basic 專案，請按一下**專案**功能表，然後再按一下**屬性**。  
  
    1.  在**編譯**屬性頁上，按一下 **進階編譯選項**，然後選取 在.NET Framework 3.5**目標 Framework （所有組態）** 下拉式清單。  
  
4.  在**專案**功能表上，按一下 **加入參考**，按一下  **.NET**索引標籤上，向下捲動至**System.Core**，按一下它，然後按  **確定**。  
  
5.  將 `using` 的 <xref:System.Linq> 指示詞或匯入的命名空間加入至您的原始程式碼檔或專案。  
  
     如需詳細資訊，請參閱[using 指示詞](~/docs/csharp/language-reference/keywords/using-directive.md)或[如何： 加入或移除已匯入命名空間 (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)。  
  
### <a name="to-enable-linq-to-dataset-functionality"></a>若要啟用 LINQ to DataSet 功能  
  
1.  必要時，請遵循本主題先前的步驟來加入 System.Core.dll 的參考和 System.Linq 的 `using` 指示詞或匯入命名空間。  
  
2.  在 C# 或 Visual Basic 中，按一下**專案**功能表，然後再按一下**加入參考**。  
  
3.  在**加入參考**對話方塊中，按一下  **.NET**索引標籤上，如果不在最上方。 向下捲動至**System.Data**和**System.Data.DataSetExtensions** ，然後按一下 它們。 按一下**確定** 按鈕。  
  
4.  將 `using` 的 <xref:System.Data> 指示詞或匯入的命名空間加入至您的原始程式碼檔或專案。 如需詳細資訊，請參閱[using 指示詞](~/docs/csharp/language-reference/keywords/using-directive.md)或[如何： 加入或移除已匯入命名空間 (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)。  
  
5.  針對 LINQ to Dataset 功能，加入 System.Data.DataSetExtensions.dll 的參考。 如果 System.Data.dll 的參考原本不存在，請加入這項參考。  
  
6.  或者，根據您連接至資料庫的方式，加入 `using` 或 `System.Data.Common` 的 `System.Data.SqlClient` 指示詞或匯入的命名空間。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [LINQ 使用者入門](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
