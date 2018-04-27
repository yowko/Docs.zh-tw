### <a name="listsort-algorithm-changed"></a>List.Sort 演算法已變更

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.5 開始，<xref:System.Collections.Generic.List%601?displayProperty=name> 的排序演算法已變更 (變更為內省式排序，而不是快速排序)。 <xref:System.Collections.Generic.List%601?displayProperty=name> 的排序從未穩定，但這項變更可能會導致不同的案例以不穩定的方式排序。 這只是表示對等項目可能會在 API 的後續呼叫中以不同的順序排序。|
|建議|因為舊的排序演算法也不穩定 (儘管方式略有不同)，應該沒有任何程式碼相依於一律以特定順序排序的對等項目。 如果有程式碼的執行個體相依於該項目，且湊巧使用舊行為，該程式碼應該更新為使用將明確地以所需順序排序項目的比較子。|
|範圍|透明|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|

