---
title: HOW TO：提供檔案作業的進度對話方塊 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 13f924566df0d7fe601e32bfe74878c18d8e64b8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245385"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>HOW TO：提供檔案作業的進度對話方塊 (C# 程式設計手冊)
如果您在 <xref:Microsoft.VisualBasic?displayProperty=nameWithType> 命名空間中使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> 方法，則可以提供標準對話方塊，以在 Windows 中顯示檔案作業進度。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>在 Visual Studio 中加入參考  
  
1.  在功能表列上，選擇 **[專案]**、**[加入參考]**。  
  
     [參考管理員] 對話方塊隨即顯示。  
  
2.  在 [組件] 區域中，選擇 [Framework] (如果尚未選擇)。  
  
3.  在名稱清單中，選取 **[Microsoft.VisualBasic]** 核取方塊，然後選擇 **[確定]** 按鈕以關閉對話方塊。  
  
## <a name="example"></a>範例  
 下列程式碼會將 `sourcePath` 指定的目錄複製到 `destinationPath` 指定的目錄。 此程式碼也會提供標準對話方塊，來顯示作業完成前的預估剩餘時間量。  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [檔案系統和登錄 (C# 程式設計指南)](../../../csharp/programming-guide/file-system/index.md)
