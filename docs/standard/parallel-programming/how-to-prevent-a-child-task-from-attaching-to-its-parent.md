---
title: 作法：防止子工作附加到其父代
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55b9c6c7175d8c7c33d8bfa03330c8e4b8816531
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592019"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>作法：防止子工作附加到其父代
本文件將示範如何防止將子工作附加至父工作。 如果您呼叫的元件是由協力廠商所撰寫，而且也會使用工作，則防止子工作附加至其父代會很實用。 例如，如果使用 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> 選項建立 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 物件的協力廠商元件會長時間執行或擲回未處理的例外狀況，則可能造成程式碼發生問題。  
  
## <a name="example"></a>範例  
 下列範例會比較使用預設選項的效果，以及防止子工作附加至父工作的效果。 這個範例會建立 <xref:System.Threading.Tasks.Task> 物件，該物件會呼叫同樣使用 <xref:System.Threading.Tasks.Task> 物件的協力廠商程式庫。 協力廠商程式庫會使用 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> 選項建立 <xref:System.Threading.Tasks.Task> 物件。 應用程式會使用 <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> 選項建立父工作。 這個選項會指示執行階段移除子工作中的 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> 規格。  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 由於父工作會在所有子工作完成後才完成，因此長時間執行的子工作可能造成整個應用程式效能不佳。 在這個範例中，當應用程式使用預設選項建立父工作時，子工作必須在父工作完成之前完成。 當應用程式使用 <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> 選項時，子工作不會附加至父工作。 因此，應用程式可以在父工作完成之後，以及必須等候子工作完成之前執行其他工作。  
  
## <a name="see-also"></a>另請參閱

- [以工作為基礎的非同步程式設計](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
