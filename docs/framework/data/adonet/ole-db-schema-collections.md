---
title: OLE DB 結構描述集合
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6c3441e86d4c5267418cf8002ba17d539c464d5c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645903"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="669c6-102">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="669c6-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="669c6-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 OLE DB 提供者的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="669c6-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="669c6-104">Microsoft SQL Server OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="669c6-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="669c6-105">Microsoft SQL Server OLE DB 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="669c6-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="669c6-106">資料表</span><span class="sxs-lookup"><span data-stu-id="669c6-106">Tables</span></span>  
  
- <span data-ttu-id="669c6-107">資料行</span><span class="sxs-lookup"><span data-stu-id="669c6-107">Columns</span></span>  
  
- <span data-ttu-id="669c6-108">程序</span><span class="sxs-lookup"><span data-stu-id="669c6-108">Procedures</span></span>  
  
- <span data-ttu-id="669c6-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="669c6-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="669c6-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="669c6-110">Catalog</span></span>  
  
- <span data-ttu-id="669c6-111">索引</span><span class="sxs-lookup"><span data-stu-id="669c6-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="669c6-112">資料表</span><span class="sxs-lookup"><span data-stu-id="669c6-112">Tables</span></span>  
  
|<span data-ttu-id="669c6-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-113">ColumnName</span></span>|<span data-ttu-id="669c6-114">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-115">TABLE_CATALOG</span></span>|<span data-ttu-id="669c6-116">String</span><span class="sxs-lookup"><span data-stu-id="669c6-116">String</span></span>|  
|<span data-ttu-id="669c6-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="669c6-118">String</span><span class="sxs-lookup"><span data-stu-id="669c6-118">String</span></span>|  
|<span data-ttu-id="669c6-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-119">TABLE_NAME</span></span>|<span data-ttu-id="669c6-120">String</span><span class="sxs-lookup"><span data-stu-id="669c6-120">String</span></span>|  
|<span data-ttu-id="669c6-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-121">TABLE_TYPE</span></span>|<span data-ttu-id="669c6-122">String</span><span class="sxs-lookup"><span data-stu-id="669c6-122">String</span></span>|  
|<span data-ttu-id="669c6-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-123">TABLE_GUID</span></span>|<span data-ttu-id="669c6-124">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-124">Guid</span></span>|  
|<span data-ttu-id="669c6-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-125">DESCRIPTION</span></span>|<span data-ttu-id="669c6-126">String</span><span class="sxs-lookup"><span data-stu-id="669c6-126">String</span></span>|  
|<span data-ttu-id="669c6-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="669c6-127">TABLE_PROPID</span></span>|<span data-ttu-id="669c6-128">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-128">Int64</span></span>|  
|<span data-ttu-id="669c6-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="669c6-129">DATE_CREATED</span></span>|<span data-ttu-id="669c6-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-130">DateTime</span></span>|  
|<span data-ttu-id="669c6-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="669c6-131">DATE_MODIFIED</span></span>|<span data-ttu-id="669c6-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="669c6-133">資料行</span><span class="sxs-lookup"><span data-stu-id="669c6-133">Columns</span></span>  
  
|<span data-ttu-id="669c6-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-134">ColumnName</span></span>|<span data-ttu-id="669c6-135">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-136">TABLE_CATALOG</span></span>|<span data-ttu-id="669c6-137">String</span><span class="sxs-lookup"><span data-stu-id="669c6-137">String</span></span>|  
|<span data-ttu-id="669c6-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="669c6-139">String</span><span class="sxs-lookup"><span data-stu-id="669c6-139">String</span></span>|  
|<span data-ttu-id="669c6-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-140">TABLE_NAME</span></span>|<span data-ttu-id="669c6-141">String</span><span class="sxs-lookup"><span data-stu-id="669c6-141">String</span></span>|  
|<span data-ttu-id="669c6-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-142">COLUMN_NAME</span></span>|<span data-ttu-id="669c6-143">String</span><span class="sxs-lookup"><span data-stu-id="669c6-143">String</span></span>|  
|<span data-ttu-id="669c6-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-144">COLUMN_GUID</span></span>|<span data-ttu-id="669c6-145">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-145">Guid</span></span>|  
|<span data-ttu-id="669c6-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="669c6-146">COLUMN_PROPID</span></span>|<span data-ttu-id="669c6-147">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-147">Int64</span></span>|  
|<span data-ttu-id="669c6-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="669c6-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="669c6-149">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-149">Int64</span></span>|  
|<span data-ttu-id="669c6-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="669c6-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="669c6-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-151">Boolean</span></span>|  
|<span data-ttu-id="669c6-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="669c6-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="669c6-153">String</span><span class="sxs-lookup"><span data-stu-id="669c6-153">String</span></span>|  
|<span data-ttu-id="669c6-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="669c6-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="669c6-155">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-155">Int64</span></span>|  
|<span data-ttu-id="669c6-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="669c6-156">IS_NULLABLE</span></span>|<span data-ttu-id="669c6-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-157">Boolean</span></span>|  
|<span data-ttu-id="669c6-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-158">DATA_TYPE</span></span>|<span data-ttu-id="669c6-159">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-159">Int32</span></span>|  
|<span data-ttu-id="669c6-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-160">TYPE_GUID</span></span>|<span data-ttu-id="669c6-161">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-161">Guid</span></span>|  
|<span data-ttu-id="669c6-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="669c6-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="669c6-163">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-163">Int64</span></span>|  
|<span data-ttu-id="669c6-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="669c6-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="669c6-165">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-165">Int64</span></span>|  
|<span data-ttu-id="669c6-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="669c6-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="669c6-167">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-167">Int32</span></span>|  
|<span data-ttu-id="669c6-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="669c6-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="669c6-169">Int16</span><span class="sxs-lookup"><span data-stu-id="669c6-169">Int16</span></span>|  
|<span data-ttu-id="669c6-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="669c6-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="669c6-171">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-171">Int64</span></span>|  
|<span data-ttu-id="669c6-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="669c6-173">String</span><span class="sxs-lookup"><span data-stu-id="669c6-173">String</span></span>|  
|<span data-ttu-id="669c6-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="669c6-175">String</span><span class="sxs-lookup"><span data-stu-id="669c6-175">String</span></span>|  
|<span data-ttu-id="669c6-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="669c6-177">String</span><span class="sxs-lookup"><span data-stu-id="669c6-177">String</span></span>|  
|<span data-ttu-id="669c6-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="669c6-179">String</span><span class="sxs-lookup"><span data-stu-id="669c6-179">String</span></span>|  
|<span data-ttu-id="669c6-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="669c6-181">String</span><span class="sxs-lookup"><span data-stu-id="669c6-181">String</span></span>|  
|<span data-ttu-id="669c6-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-182">COLLATION_NAME</span></span>|<span data-ttu-id="669c6-183">String</span><span class="sxs-lookup"><span data-stu-id="669c6-183">String</span></span>|  
|<span data-ttu-id="669c6-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="669c6-185">String</span><span class="sxs-lookup"><span data-stu-id="669c6-185">String</span></span>|  
|<span data-ttu-id="669c6-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="669c6-187">String</span><span class="sxs-lookup"><span data-stu-id="669c6-187">String</span></span>|  
|<span data-ttu-id="669c6-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-188">DOMAIN_NAME</span></span>|<span data-ttu-id="669c6-189">String</span><span class="sxs-lookup"><span data-stu-id="669c6-189">String</span></span>|  
|<span data-ttu-id="669c6-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-190">DESCRIPTION</span></span>|<span data-ttu-id="669c6-191">String</span><span class="sxs-lookup"><span data-stu-id="669c6-191">String</span></span>|  
|<span data-ttu-id="669c6-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="669c6-192">COLUMN_LCID</span></span>|<span data-ttu-id="669c6-193">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-193">Int32</span></span>|  
|<span data-ttu-id="669c6-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="669c6-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="669c6-195">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-195">Int32</span></span>|  
|<span data-ttu-id="669c6-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="669c6-196">COLUMN_SORTID</span></span>|<span data-ttu-id="669c6-197">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-197">Int32</span></span>|  
|<span data-ttu-id="669c6-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="669c6-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="669c6-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="669c6-199">Byte[]</span></span>|  
|<span data-ttu-id="669c6-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="669c6-200">IS_COMPUTED</span></span>|<span data-ttu-id="669c6-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="669c6-202">程序</span><span class="sxs-lookup"><span data-stu-id="669c6-202">Procedures</span></span>  
  
|<span data-ttu-id="669c6-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-203">ColumnName</span></span>|<span data-ttu-id="669c6-204">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="669c6-206">String</span><span class="sxs-lookup"><span data-stu-id="669c6-206">String</span></span>|  
|<span data-ttu-id="669c6-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="669c6-208">String</span><span class="sxs-lookup"><span data-stu-id="669c6-208">String</span></span>|  
|<span data-ttu-id="669c6-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="669c6-210">String</span><span class="sxs-lookup"><span data-stu-id="669c6-210">String</span></span>|  
|<span data-ttu-id="669c6-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="669c6-212">Int16</span><span class="sxs-lookup"><span data-stu-id="669c6-212">Int16</span></span>|  
|<span data-ttu-id="669c6-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="669c6-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="669c6-214">String</span><span class="sxs-lookup"><span data-stu-id="669c6-214">String</span></span>|  
|<span data-ttu-id="669c6-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-215">DESCRIPTION</span></span>|<span data-ttu-id="669c6-216">String</span><span class="sxs-lookup"><span data-stu-id="669c6-216">String</span></span>|  
|<span data-ttu-id="669c6-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="669c6-217">DATE_CREATED</span></span>|<span data-ttu-id="669c6-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-218">DateTime</span></span>|  
|<span data-ttu-id="669c6-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="669c6-219">DATE_MODIFIED</span></span>|<span data-ttu-id="669c6-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="669c6-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="669c6-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="669c6-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-222">ColumnName</span></span>|<span data-ttu-id="669c6-223">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="669c6-225">String</span><span class="sxs-lookup"><span data-stu-id="669c6-225">String</span></span>|  
|<span data-ttu-id="669c6-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="669c6-227">String</span><span class="sxs-lookup"><span data-stu-id="669c6-227">String</span></span>|  
|<span data-ttu-id="669c6-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="669c6-229">String</span><span class="sxs-lookup"><span data-stu-id="669c6-229">String</span></span>|  
|<span data-ttu-id="669c6-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-230">PARAMETER_NAME</span></span>|<span data-ttu-id="669c6-231">String</span><span class="sxs-lookup"><span data-stu-id="669c6-231">String</span></span>|  
|<span data-ttu-id="669c6-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="669c6-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="669c6-233">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-233">Int32</span></span>|  
|<span data-ttu-id="669c6-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="669c6-235">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-235">Int32</span></span>|  
|<span data-ttu-id="669c6-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="669c6-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="669c6-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-237">Boolean</span></span>|  
|<span data-ttu-id="669c6-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="669c6-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="669c6-239">String</span><span class="sxs-lookup"><span data-stu-id="669c6-239">String</span></span>|  
|<span data-ttu-id="669c6-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="669c6-240">IS_NULLABLE</span></span>|<span data-ttu-id="669c6-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-241">Boolean</span></span>|  
|<span data-ttu-id="669c6-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-242">DATA_TYPE</span></span>|<span data-ttu-id="669c6-243">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-243">Int32</span></span>|  
|<span data-ttu-id="669c6-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="669c6-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="669c6-245">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-245">Int64</span></span>|  
|<span data-ttu-id="669c6-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="669c6-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="669c6-247">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-247">Int64</span></span>|  
|<span data-ttu-id="669c6-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="669c6-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="669c6-249">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-249">Int32</span></span>|  
|<span data-ttu-id="669c6-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="669c6-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="669c6-251">Int16</span><span class="sxs-lookup"><span data-stu-id="669c6-251">Int16</span></span>|  
|<span data-ttu-id="669c6-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-252">DESCRIPTION</span></span>|<span data-ttu-id="669c6-253">String</span><span class="sxs-lookup"><span data-stu-id="669c6-253">String</span></span>|  
|<span data-ttu-id="669c6-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-254">TYPE_NAME</span></span>|<span data-ttu-id="669c6-255">String</span><span class="sxs-lookup"><span data-stu-id="669c6-255">String</span></span>|  
|<span data-ttu-id="669c6-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="669c6-257">String</span><span class="sxs-lookup"><span data-stu-id="669c6-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="669c6-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="669c6-258">Catalog</span></span>  
  
|<span data-ttu-id="669c6-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-259">ColumnName</span></span>|<span data-ttu-id="669c6-260">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-261">CATALOG_NAME</span></span>|<span data-ttu-id="669c6-262">String</span><span class="sxs-lookup"><span data-stu-id="669c6-262">String</span></span>|  
|<span data-ttu-id="669c6-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-263">DESCRIPTION</span></span>|<span data-ttu-id="669c6-264">String</span><span class="sxs-lookup"><span data-stu-id="669c6-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="669c6-265">索引</span><span class="sxs-lookup"><span data-stu-id="669c6-265">Indexes</span></span>  
  
|<span data-ttu-id="669c6-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-266">ColumnName</span></span>|<span data-ttu-id="669c6-267">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-268">TABLE_CATALOG</span></span>|<span data-ttu-id="669c6-269">String</span><span class="sxs-lookup"><span data-stu-id="669c6-269">String</span></span>|  
|<span data-ttu-id="669c6-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="669c6-271">String</span><span class="sxs-lookup"><span data-stu-id="669c6-271">String</span></span>|  
|<span data-ttu-id="669c6-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-272">TABLE_NAME</span></span>|<span data-ttu-id="669c6-273">String</span><span class="sxs-lookup"><span data-stu-id="669c6-273">String</span></span>|  
|<span data-ttu-id="669c6-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-274">INDEX_CATALOG</span></span>|<span data-ttu-id="669c6-275">String</span><span class="sxs-lookup"><span data-stu-id="669c6-275">String</span></span>|  
|<span data-ttu-id="669c6-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="669c6-277">String</span><span class="sxs-lookup"><span data-stu-id="669c6-277">String</span></span>|  
|<span data-ttu-id="669c6-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-278">INDEX_NAME</span></span>|<span data-ttu-id="669c6-279">String</span><span class="sxs-lookup"><span data-stu-id="669c6-279">String</span></span>|  
|<span data-ttu-id="669c6-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="669c6-280">PRIMARY_KEY</span></span>|<span data-ttu-id="669c6-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-281">Boolean</span></span>|  
|<span data-ttu-id="669c6-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="669c6-282">UNIQUE</span></span>|<span data-ttu-id="669c6-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-283">Boolean</span></span>|  
|<span data-ttu-id="669c6-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="669c6-284">CLUSTERED</span></span>|<span data-ttu-id="669c6-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-285">Boolean</span></span>|  
|<span data-ttu-id="669c6-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-286">TYPE</span></span>|<span data-ttu-id="669c6-287">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-287">Int32</span></span>|  
|<span data-ttu-id="669c6-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="669c6-288">FILL_FACTOR</span></span>|<span data-ttu-id="669c6-289">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-289">Int32</span></span>|  
|<span data-ttu-id="669c6-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="669c6-290">INITIAL_SIZE</span></span>|<span data-ttu-id="669c6-291">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-291">Int32</span></span>|  
|<span data-ttu-id="669c6-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="669c6-292">NULLS</span></span>|<span data-ttu-id="669c6-293">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-293">Int32</span></span>|  
|<span data-ttu-id="669c6-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="669c6-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="669c6-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-295">Boolean</span></span>|  
|<span data-ttu-id="669c6-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="669c6-296">AUTO_UPDATE</span></span>|<span data-ttu-id="669c6-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-297">Boolean</span></span>|  
|<span data-ttu-id="669c6-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="669c6-298">NULL_COLLATION</span></span>|<span data-ttu-id="669c6-299">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-299">Int32</span></span>|  
|<span data-ttu-id="669c6-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="669c6-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="669c6-301">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-301">Int64</span></span>|  
|<span data-ttu-id="669c6-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-302">COLUMN_NAME</span></span>|<span data-ttu-id="669c6-303">String</span><span class="sxs-lookup"><span data-stu-id="669c6-303">String</span></span>|  
|<span data-ttu-id="669c6-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-304">COLUMN_GUID</span></span>|<span data-ttu-id="669c6-305">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-305">Guid</span></span>|  
|<span data-ttu-id="669c6-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="669c6-306">COLUMN_PROPID</span></span>|<span data-ttu-id="669c6-307">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-307">Int64</span></span>|  
|<span data-ttu-id="669c6-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="669c6-308">COLLATION</span></span>|<span data-ttu-id="669c6-309">Int16</span><span class="sxs-lookup"><span data-stu-id="669c6-309">Int16</span></span>|  
|<span data-ttu-id="669c6-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="669c6-310">CARDINALITY</span></span>|<span data-ttu-id="669c6-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="669c6-311">Decimal</span></span>|  
|<span data-ttu-id="669c6-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="669c6-312">PAGES</span></span>|<span data-ttu-id="669c6-313">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-313">Int32</span></span>|  
|<span data-ttu-id="669c6-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="669c6-314">FILTER_CONDITION</span></span>|<span data-ttu-id="669c6-315">String</span><span class="sxs-lookup"><span data-stu-id="669c6-315">String</span></span>|  
|<span data-ttu-id="669c6-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="669c6-316">INTEGRATED</span></span>|<span data-ttu-id="669c6-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="669c6-318">Microsoft Oracle OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="669c6-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="669c6-319">除了通用結構描述集合之外，Microsoft Oracle OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="669c6-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="669c6-320">資料表</span><span class="sxs-lookup"><span data-stu-id="669c6-320">Tables</span></span>  
  
- <span data-ttu-id="669c6-321">資料行</span><span class="sxs-lookup"><span data-stu-id="669c6-321">Columns</span></span>  
  
- <span data-ttu-id="669c6-322">程序</span><span class="sxs-lookup"><span data-stu-id="669c6-322">Procedures</span></span>  
  
- <span data-ttu-id="669c6-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="669c6-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="669c6-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="669c6-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="669c6-325">檢視</span><span class="sxs-lookup"><span data-stu-id="669c6-325">Views</span></span>  
  
- <span data-ttu-id="669c6-326">索引</span><span class="sxs-lookup"><span data-stu-id="669c6-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="669c6-327">資料表</span><span class="sxs-lookup"><span data-stu-id="669c6-327">Tables</span></span>  
  
|<span data-ttu-id="669c6-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-328">ColumnName</span></span>|<span data-ttu-id="669c6-329">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-330">TABLE_CATALOG</span></span>|<span data-ttu-id="669c6-331">String</span><span class="sxs-lookup"><span data-stu-id="669c6-331">String</span></span>|  
|<span data-ttu-id="669c6-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="669c6-333">String</span><span class="sxs-lookup"><span data-stu-id="669c6-333">String</span></span>|  
|<span data-ttu-id="669c6-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-334">TABLE_NAME</span></span>|<span data-ttu-id="669c6-335">String</span><span class="sxs-lookup"><span data-stu-id="669c6-335">String</span></span>|  
|<span data-ttu-id="669c6-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-336">TABLE_TYPE</span></span>|<span data-ttu-id="669c6-337">String</span><span class="sxs-lookup"><span data-stu-id="669c6-337">String</span></span>|  
|<span data-ttu-id="669c6-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-338">TABLE_GUID</span></span>|<span data-ttu-id="669c6-339">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-339">Guid</span></span>|  
|<span data-ttu-id="669c6-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-340">DESCRIPTION</span></span>|<span data-ttu-id="669c6-341">String</span><span class="sxs-lookup"><span data-stu-id="669c6-341">String</span></span>|  
|<span data-ttu-id="669c6-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="669c6-342">TABLE_PROPID</span></span>|<span data-ttu-id="669c6-343">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-343">Int64</span></span>|  
|<span data-ttu-id="669c6-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="669c6-344">DATE_CREATED</span></span>|<span data-ttu-id="669c6-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-345">DateTime</span></span>|  
|<span data-ttu-id="669c6-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="669c6-346">DATE_MODIFIED</span></span>|<span data-ttu-id="669c6-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="669c6-348">資料行</span><span class="sxs-lookup"><span data-stu-id="669c6-348">Columns</span></span>  
  
|<span data-ttu-id="669c6-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-349">ColumnName</span></span>|<span data-ttu-id="669c6-350">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-351">TABLE_CATALOG</span></span>|<span data-ttu-id="669c6-352">String</span><span class="sxs-lookup"><span data-stu-id="669c6-352">String</span></span>|  
|<span data-ttu-id="669c6-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="669c6-354">String</span><span class="sxs-lookup"><span data-stu-id="669c6-354">String</span></span>|  
|<span data-ttu-id="669c6-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-355">TABLE_NAME</span></span>|<span data-ttu-id="669c6-356">String</span><span class="sxs-lookup"><span data-stu-id="669c6-356">String</span></span>|  
|<span data-ttu-id="669c6-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-357">COLUMN_NAME</span></span>|<span data-ttu-id="669c6-358">String</span><span class="sxs-lookup"><span data-stu-id="669c6-358">String</span></span>|  
|<span data-ttu-id="669c6-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-359">COLUMN_GUID</span></span>|<span data-ttu-id="669c6-360">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-360">Guid</span></span>|  
|<span data-ttu-id="669c6-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="669c6-361">COLUMN_PROPID</span></span>|<span data-ttu-id="669c6-362">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-362">Int64</span></span>|  
|<span data-ttu-id="669c6-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="669c6-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="669c6-364">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-364">Int64</span></span>|  
|<span data-ttu-id="669c6-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="669c6-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="669c6-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-366">Boolean</span></span>|  
|<span data-ttu-id="669c6-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="669c6-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="669c6-368">String</span><span class="sxs-lookup"><span data-stu-id="669c6-368">String</span></span>|  
|<span data-ttu-id="669c6-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="669c6-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="669c6-370">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-370">Int64</span></span>|  
|<span data-ttu-id="669c6-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="669c6-371">IS_NULLABLE</span></span>|<span data-ttu-id="669c6-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-372">Boolean</span></span>|  
|<span data-ttu-id="669c6-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-373">DATA_TYPE</span></span>|<span data-ttu-id="669c6-374">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-374">Int32</span></span>|  
|<span data-ttu-id="669c6-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-375">TYPE_GUID</span></span>|<span data-ttu-id="669c6-376">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-376">Guid</span></span>|  
|<span data-ttu-id="669c6-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="669c6-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="669c6-378">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-378">Int64</span></span>|  
|<span data-ttu-id="669c6-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="669c6-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="669c6-380">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-380">Int64</span></span>|  
|<span data-ttu-id="669c6-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="669c6-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="669c6-382">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-382">Int32</span></span>|  
|<span data-ttu-id="669c6-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="669c6-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="669c6-384">Int16</span><span class="sxs-lookup"><span data-stu-id="669c6-384">Int16</span></span>|  
|<span data-ttu-id="669c6-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="669c6-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="669c6-386">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-386">Int64</span></span>|  
|<span data-ttu-id="669c6-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="669c6-388">String</span><span class="sxs-lookup"><span data-stu-id="669c6-388">String</span></span>|  
|<span data-ttu-id="669c6-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="669c6-390">String</span><span class="sxs-lookup"><span data-stu-id="669c6-390">String</span></span>|  
|<span data-ttu-id="669c6-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="669c6-392">String</span><span class="sxs-lookup"><span data-stu-id="669c6-392">String</span></span>|  
|<span data-ttu-id="669c6-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="669c6-394">String</span><span class="sxs-lookup"><span data-stu-id="669c6-394">String</span></span>|  
|<span data-ttu-id="669c6-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="669c6-396">String</span><span class="sxs-lookup"><span data-stu-id="669c6-396">String</span></span>|  
|<span data-ttu-id="669c6-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-397">COLLATION_NAME</span></span>|<span data-ttu-id="669c6-398">String</span><span class="sxs-lookup"><span data-stu-id="669c6-398">String</span></span>|  
|<span data-ttu-id="669c6-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="669c6-400">String</span><span class="sxs-lookup"><span data-stu-id="669c6-400">String</span></span>|  
|<span data-ttu-id="669c6-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="669c6-402">String</span><span class="sxs-lookup"><span data-stu-id="669c6-402">String</span></span>|  
|<span data-ttu-id="669c6-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-403">DOMAIN_NAME</span></span>|<span data-ttu-id="669c6-404">String</span><span class="sxs-lookup"><span data-stu-id="669c6-404">String</span></span>|  
|<span data-ttu-id="669c6-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-405">DESCRIPTION</span></span>|<span data-ttu-id="669c6-406">String</span><span class="sxs-lookup"><span data-stu-id="669c6-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="669c6-407">程序</span><span class="sxs-lookup"><span data-stu-id="669c6-407">Procedures</span></span>  
  
|<span data-ttu-id="669c6-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-408">ColumnName</span></span>|<span data-ttu-id="669c6-409">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="669c6-411">String</span><span class="sxs-lookup"><span data-stu-id="669c6-411">String</span></span>|  
|<span data-ttu-id="669c6-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="669c6-413">String</span><span class="sxs-lookup"><span data-stu-id="669c6-413">String</span></span>|  
|<span data-ttu-id="669c6-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="669c6-415">String</span><span class="sxs-lookup"><span data-stu-id="669c6-415">String</span></span>|  
|<span data-ttu-id="669c6-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="669c6-417">Int16</span><span class="sxs-lookup"><span data-stu-id="669c6-417">Int16</span></span>|  
|<span data-ttu-id="669c6-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="669c6-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="669c6-419">String</span><span class="sxs-lookup"><span data-stu-id="669c6-419">String</span></span>|  
|<span data-ttu-id="669c6-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-420">DESCRIPTION</span></span>|<span data-ttu-id="669c6-421">String</span><span class="sxs-lookup"><span data-stu-id="669c6-421">String</span></span>|  
|<span data-ttu-id="669c6-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="669c6-422">DATE_CREATED</span></span>|<span data-ttu-id="669c6-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-423">DateTime</span></span>|  
|<span data-ttu-id="669c6-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="669c6-424">DATE_MODIFIED</span></span>|<span data-ttu-id="669c6-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="669c6-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="669c6-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="669c6-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-427">ColumnName</span></span>|<span data-ttu-id="669c6-428">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="669c6-430">String</span><span class="sxs-lookup"><span data-stu-id="669c6-430">String</span></span>|  
|<span data-ttu-id="669c6-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="669c6-432">String</span><span class="sxs-lookup"><span data-stu-id="669c6-432">String</span></span>|  
|<span data-ttu-id="669c6-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="669c6-434">String</span><span class="sxs-lookup"><span data-stu-id="669c6-434">String</span></span>|  
|<span data-ttu-id="669c6-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-435">COLUMN_NAME</span></span>|<span data-ttu-id="669c6-436">String</span><span class="sxs-lookup"><span data-stu-id="669c6-436">String</span></span>|  
|<span data-ttu-id="669c6-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-437">COLUMN_GUID</span></span>|<span data-ttu-id="669c6-438">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-438">Guid</span></span>|  
|<span data-ttu-id="669c6-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="669c6-439">COLUMN_PROPID</span></span>|<span data-ttu-id="669c6-440">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-440">Int64</span></span>|  
|<span data-ttu-id="669c6-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="669c6-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="669c6-442">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-442">Int64</span></span>|  
|<span data-ttu-id="669c6-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="669c6-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="669c6-444">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-444">Int64</span></span>|  
|<span data-ttu-id="669c6-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="669c6-445">IS_NULLABLE</span></span>|<span data-ttu-id="669c6-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-446">Boolean</span></span>|  
|<span data-ttu-id="669c6-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-447">DATA_TYPE</span></span>|<span data-ttu-id="669c6-448">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-448">Int32</span></span>|  
|<span data-ttu-id="669c6-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-449">TYPE_GUID</span></span>|<span data-ttu-id="669c6-450">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-450">Guid</span></span>|  
|<span data-ttu-id="669c6-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="669c6-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="669c6-452">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-452">Int64</span></span>|  
|<span data-ttu-id="669c6-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="669c6-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="669c6-454">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-454">Int64</span></span>|  
|<span data-ttu-id="669c6-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="669c6-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="669c6-456">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-456">Int32</span></span>|  
|<span data-ttu-id="669c6-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="669c6-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="669c6-458">Int16</span><span class="sxs-lookup"><span data-stu-id="669c6-458">Int16</span></span>|  
|<span data-ttu-id="669c6-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-459">DESCRIPTION</span></span>|<span data-ttu-id="669c6-460">String</span><span class="sxs-lookup"><span data-stu-id="669c6-460">String</span></span>|  
|<span data-ttu-id="669c6-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="669c6-461">OVERLOAD</span></span>|<span data-ttu-id="669c6-462">Int16</span><span class="sxs-lookup"><span data-stu-id="669c6-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="669c6-463">檢視</span><span class="sxs-lookup"><span data-stu-id="669c6-463">Views</span></span>  
  
|<span data-ttu-id="669c6-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-464">ColumnName</span></span>|<span data-ttu-id="669c6-465">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-466">TABLE_CATALOG</span></span>|<span data-ttu-id="669c6-467">String</span><span class="sxs-lookup"><span data-stu-id="669c6-467">String</span></span>|  
|<span data-ttu-id="669c6-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="669c6-469">String</span><span class="sxs-lookup"><span data-stu-id="669c6-469">String</span></span>|  
|<span data-ttu-id="669c6-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-470">TABLE_NAME</span></span>|<span data-ttu-id="669c6-471">String</span><span class="sxs-lookup"><span data-stu-id="669c6-471">String</span></span>|  
|<span data-ttu-id="669c6-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="669c6-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="669c6-473">String</span><span class="sxs-lookup"><span data-stu-id="669c6-473">String</span></span>|  
|<span data-ttu-id="669c6-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-474">CHECK_OPTION</span></span>|<span data-ttu-id="669c6-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-475">Boolean</span></span>|  
|<span data-ttu-id="669c6-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="669c6-476">IS_UPDATABLE</span></span>|<span data-ttu-id="669c6-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-477">Boolean</span></span>|  
|<span data-ttu-id="669c6-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-478">DESCRIPTION</span></span>|<span data-ttu-id="669c6-479">String</span><span class="sxs-lookup"><span data-stu-id="669c6-479">String</span></span>|  
|<span data-ttu-id="669c6-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="669c6-480">DATE_CREATED</span></span>|<span data-ttu-id="669c6-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-481">DateTime</span></span>|  
|<span data-ttu-id="669c6-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="669c6-482">DATE_MODIFIED</span></span>|<span data-ttu-id="669c6-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="669c6-484">索引</span><span class="sxs-lookup"><span data-stu-id="669c6-484">Indexes</span></span>  
  
|<span data-ttu-id="669c6-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-485">ColumnName</span></span>|<span data-ttu-id="669c6-486">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-487">TABLE_CATALOG</span></span>|<span data-ttu-id="669c6-488">String</span><span class="sxs-lookup"><span data-stu-id="669c6-488">String</span></span>|  
|<span data-ttu-id="669c6-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="669c6-490">String</span><span class="sxs-lookup"><span data-stu-id="669c6-490">String</span></span>|  
|<span data-ttu-id="669c6-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-491">TABLE_NAME</span></span>|<span data-ttu-id="669c6-492">String</span><span class="sxs-lookup"><span data-stu-id="669c6-492">String</span></span>|  
|<span data-ttu-id="669c6-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-493">INDEX_CATALOG</span></span>|<span data-ttu-id="669c6-494">String</span><span class="sxs-lookup"><span data-stu-id="669c6-494">String</span></span>|  
|<span data-ttu-id="669c6-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="669c6-496">String</span><span class="sxs-lookup"><span data-stu-id="669c6-496">String</span></span>|  
|<span data-ttu-id="669c6-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-497">INDEX_NAME</span></span>|<span data-ttu-id="669c6-498">String</span><span class="sxs-lookup"><span data-stu-id="669c6-498">String</span></span>|  
|<span data-ttu-id="669c6-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="669c6-499">PRIMARY_KEY</span></span>|<span data-ttu-id="669c6-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-500">Boolean</span></span>|  
|<span data-ttu-id="669c6-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="669c6-501">UNIQUE</span></span>|<span data-ttu-id="669c6-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-502">Boolean</span></span>|  
|<span data-ttu-id="669c6-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="669c6-503">CLUSTERED</span></span>|<span data-ttu-id="669c6-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-504">Boolean</span></span>|  
|<span data-ttu-id="669c6-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-505">TYPE</span></span>|<span data-ttu-id="669c6-506">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-506">Int32</span></span>|  
|<span data-ttu-id="669c6-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="669c6-507">FILL_FACTOR</span></span>|<span data-ttu-id="669c6-508">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-508">Int32</span></span>|  
|<span data-ttu-id="669c6-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="669c6-509">INITIAL_SIZE</span></span>|<span data-ttu-id="669c6-510">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-510">Int32</span></span>|  
|<span data-ttu-id="669c6-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="669c6-511">NULLS</span></span>|<span data-ttu-id="669c6-512">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-512">Int32</span></span>|  
|<span data-ttu-id="669c6-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="669c6-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="669c6-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-514">Boolean</span></span>|  
|<span data-ttu-id="669c6-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="669c6-515">AUTO_UPDATE</span></span>|<span data-ttu-id="669c6-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-516">Boolean</span></span>|  
|<span data-ttu-id="669c6-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="669c6-517">NULL_COLLATION</span></span>|<span data-ttu-id="669c6-518">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-518">Int32</span></span>|  
|<span data-ttu-id="669c6-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="669c6-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="669c6-520">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-520">Int64</span></span>|  
|<span data-ttu-id="669c6-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-521">COLUMN_NAME</span></span>|<span data-ttu-id="669c6-522">String</span><span class="sxs-lookup"><span data-stu-id="669c6-522">String</span></span>|  
|<span data-ttu-id="669c6-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-523">COLUMN_GUID</span></span>|<span data-ttu-id="669c6-524">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-524">Guid</span></span>|  
|<span data-ttu-id="669c6-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="669c6-525">COLUMN_PROPID</span></span>|<span data-ttu-id="669c6-526">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-526">Int64</span></span>|  
|<span data-ttu-id="669c6-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="669c6-527">COLLATION</span></span>|<span data-ttu-id="669c6-528">Int16</span><span class="sxs-lookup"><span data-stu-id="669c6-528">Int16</span></span>|  
|<span data-ttu-id="669c6-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="669c6-529">CARDINALITY</span></span>|<span data-ttu-id="669c6-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="669c6-530">Decimal</span></span>|  
|<span data-ttu-id="669c6-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="669c6-531">PAGES</span></span>|<span data-ttu-id="669c6-532">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-532">Int32</span></span>|  
|<span data-ttu-id="669c6-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="669c6-533">FILTER_CONDITION</span></span>|<span data-ttu-id="669c6-534">String</span><span class="sxs-lookup"><span data-stu-id="669c6-534">String</span></span>|  
|<span data-ttu-id="669c6-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="669c6-535">INTEGRATED</span></span>|<span data-ttu-id="669c6-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="669c6-537">Microsoft Jet OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="669c6-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="669c6-538">除了通用結構描述集合之外，Microsoft Jet OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="669c6-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="669c6-539">資料表</span><span class="sxs-lookup"><span data-stu-id="669c6-539">Tables</span></span>  
  
- <span data-ttu-id="669c6-540">資料行</span><span class="sxs-lookup"><span data-stu-id="669c6-540">Columns</span></span>  
  
- <span data-ttu-id="669c6-541">程序</span><span class="sxs-lookup"><span data-stu-id="669c6-541">Procedures</span></span>  
  
- <span data-ttu-id="669c6-542">檢視</span><span class="sxs-lookup"><span data-stu-id="669c6-542">Views</span></span>  
  
- <span data-ttu-id="669c6-543">索引</span><span class="sxs-lookup"><span data-stu-id="669c6-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="669c6-544">資料表</span><span class="sxs-lookup"><span data-stu-id="669c6-544">Tables</span></span>  
  
|<span data-ttu-id="669c6-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-545">ColumnName</span></span>|<span data-ttu-id="669c6-546">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-547">TABLE_CATALOG</span></span>|<span data-ttu-id="669c6-548">String</span><span class="sxs-lookup"><span data-stu-id="669c6-548">String</span></span>|  
|<span data-ttu-id="669c6-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="669c6-550">String</span><span class="sxs-lookup"><span data-stu-id="669c6-550">String</span></span>|  
|<span data-ttu-id="669c6-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-551">TABLE_NAME</span></span>|<span data-ttu-id="669c6-552">String</span><span class="sxs-lookup"><span data-stu-id="669c6-552">String</span></span>|  
|<span data-ttu-id="669c6-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-553">TABLE_TYPE</span></span>|<span data-ttu-id="669c6-554">String</span><span class="sxs-lookup"><span data-stu-id="669c6-554">String</span></span>|  
|<span data-ttu-id="669c6-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-555">TABLE_GUID</span></span>|<span data-ttu-id="669c6-556">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-556">Guid</span></span>|  
|<span data-ttu-id="669c6-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-557">DESCRIPTION</span></span>|<span data-ttu-id="669c6-558">String</span><span class="sxs-lookup"><span data-stu-id="669c6-558">String</span></span>|  
|<span data-ttu-id="669c6-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="669c6-559">TABLE_PROPID</span></span>|<span data-ttu-id="669c6-560">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-560">Int64</span></span>|  
|<span data-ttu-id="669c6-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="669c6-561">DATE_CREATED</span></span>|<span data-ttu-id="669c6-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-562">DateTime</span></span>|  
|<span data-ttu-id="669c6-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="669c6-563">DATE_MODIFIED</span></span>|<span data-ttu-id="669c6-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="669c6-565">資料行</span><span class="sxs-lookup"><span data-stu-id="669c6-565">Columns</span></span>  
  
|<span data-ttu-id="669c6-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-566">ColumnName</span></span>|<span data-ttu-id="669c6-567">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-568">TABLE_CATALOG</span></span>|<span data-ttu-id="669c6-569">String</span><span class="sxs-lookup"><span data-stu-id="669c6-569">String</span></span>|  
|<span data-ttu-id="669c6-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="669c6-571">String</span><span class="sxs-lookup"><span data-stu-id="669c6-571">String</span></span>|  
|<span data-ttu-id="669c6-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-572">TABLE_NAME</span></span>|<span data-ttu-id="669c6-573">String</span><span class="sxs-lookup"><span data-stu-id="669c6-573">String</span></span>|  
|<span data-ttu-id="669c6-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-574">COLUMN_NAME</span></span>|<span data-ttu-id="669c6-575">String</span><span class="sxs-lookup"><span data-stu-id="669c6-575">String</span></span>|  
|<span data-ttu-id="669c6-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-576">COLUMN_GUID</span></span>|<span data-ttu-id="669c6-577">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-577">Guid</span></span>|  
|<span data-ttu-id="669c6-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="669c6-578">COLUMN_PROPID</span></span>|<span data-ttu-id="669c6-579">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-579">Int64</span></span>|  
|<span data-ttu-id="669c6-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="669c6-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="669c6-581">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-581">Int64</span></span>|  
|<span data-ttu-id="669c6-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="669c6-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="669c6-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-583">Boolean</span></span>|  
|<span data-ttu-id="669c6-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="669c6-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="669c6-585">String</span><span class="sxs-lookup"><span data-stu-id="669c6-585">String</span></span>|  
|<span data-ttu-id="669c6-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="669c6-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="669c6-587">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-587">Int64</span></span>|  
|<span data-ttu-id="669c6-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="669c6-588">IS_NULLABLE</span></span>|<span data-ttu-id="669c6-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-589">Boolean</span></span>|  
|<span data-ttu-id="669c6-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-590">DATA_TYPE</span></span>|<span data-ttu-id="669c6-591">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-591">Int32</span></span>|  
|<span data-ttu-id="669c6-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-592">TYPE_GUID</span></span>|<span data-ttu-id="669c6-593">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-593">Guid</span></span>|  
|<span data-ttu-id="669c6-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="669c6-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="669c6-595">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-595">Int64</span></span>|  
|<span data-ttu-id="669c6-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="669c6-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="669c6-597">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-597">Int64</span></span>|  
|<span data-ttu-id="669c6-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="669c6-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="669c6-599">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-599">Int32</span></span>|  
|<span data-ttu-id="669c6-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="669c6-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="669c6-601">Int16</span><span class="sxs-lookup"><span data-stu-id="669c6-601">Int16</span></span>|  
|<span data-ttu-id="669c6-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="669c6-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="669c6-603">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-603">Int64</span></span>|  
|<span data-ttu-id="669c6-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="669c6-605">String</span><span class="sxs-lookup"><span data-stu-id="669c6-605">String</span></span>|  
|<span data-ttu-id="669c6-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="669c6-607">String</span><span class="sxs-lookup"><span data-stu-id="669c6-607">String</span></span>|  
|<span data-ttu-id="669c6-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="669c6-609">String</span><span class="sxs-lookup"><span data-stu-id="669c6-609">String</span></span>|  
|<span data-ttu-id="669c6-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="669c6-611">String</span><span class="sxs-lookup"><span data-stu-id="669c6-611">String</span></span>|  
|<span data-ttu-id="669c6-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="669c6-613">String</span><span class="sxs-lookup"><span data-stu-id="669c6-613">String</span></span>|  
|<span data-ttu-id="669c6-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-614">COLLATION_NAME</span></span>|<span data-ttu-id="669c6-615">String</span><span class="sxs-lookup"><span data-stu-id="669c6-615">String</span></span>|  
|<span data-ttu-id="669c6-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="669c6-617">String</span><span class="sxs-lookup"><span data-stu-id="669c6-617">String</span></span>|  
|<span data-ttu-id="669c6-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="669c6-619">String</span><span class="sxs-lookup"><span data-stu-id="669c6-619">String</span></span>|  
|<span data-ttu-id="669c6-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-620">DOMAIN_NAME</span></span>|<span data-ttu-id="669c6-621">String</span><span class="sxs-lookup"><span data-stu-id="669c6-621">String</span></span>|  
|<span data-ttu-id="669c6-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-622">DESCRIPTION</span></span>|<span data-ttu-id="669c6-623">String</span><span class="sxs-lookup"><span data-stu-id="669c6-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="669c6-624">程序</span><span class="sxs-lookup"><span data-stu-id="669c6-624">Procedures</span></span>  
  
|<span data-ttu-id="669c6-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-625">ColumnName</span></span>|<span data-ttu-id="669c6-626">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="669c6-628">String</span><span class="sxs-lookup"><span data-stu-id="669c6-628">String</span></span>|  
|<span data-ttu-id="669c6-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="669c6-630">String</span><span class="sxs-lookup"><span data-stu-id="669c6-630">String</span></span>|  
|<span data-ttu-id="669c6-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="669c6-632">String</span><span class="sxs-lookup"><span data-stu-id="669c6-632">String</span></span>|  
|<span data-ttu-id="669c6-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="669c6-634">Int16</span><span class="sxs-lookup"><span data-stu-id="669c6-634">Int16</span></span>|  
|<span data-ttu-id="669c6-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="669c6-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="669c6-636">String</span><span class="sxs-lookup"><span data-stu-id="669c6-636">String</span></span>|  
|<span data-ttu-id="669c6-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-637">DESCRIPTION</span></span>|<span data-ttu-id="669c6-638">String</span><span class="sxs-lookup"><span data-stu-id="669c6-638">String</span></span>|  
|<span data-ttu-id="669c6-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="669c6-639">DATE_CREATED</span></span>|<span data-ttu-id="669c6-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-640">DateTime</span></span>|  
|<span data-ttu-id="669c6-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="669c6-641">DATE_MODIFIED</span></span>|<span data-ttu-id="669c6-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="669c6-643">檢視</span><span class="sxs-lookup"><span data-stu-id="669c6-643">Views</span></span>  
  
|<span data-ttu-id="669c6-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-644">ColumnName</span></span>|<span data-ttu-id="669c6-645">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-646">TABLE_CATALOG</span></span>|<span data-ttu-id="669c6-647">String</span><span class="sxs-lookup"><span data-stu-id="669c6-647">String</span></span>|  
|<span data-ttu-id="669c6-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="669c6-649">String</span><span class="sxs-lookup"><span data-stu-id="669c6-649">String</span></span>|  
|<span data-ttu-id="669c6-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-650">TABLE_NAME</span></span>|<span data-ttu-id="669c6-651">String</span><span class="sxs-lookup"><span data-stu-id="669c6-651">String</span></span>|  
|<span data-ttu-id="669c6-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="669c6-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="669c6-653">String</span><span class="sxs-lookup"><span data-stu-id="669c6-653">String</span></span>|  
|<span data-ttu-id="669c6-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-654">CHECK_OPTION</span></span>|<span data-ttu-id="669c6-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-655">Boolean</span></span>|  
|<span data-ttu-id="669c6-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="669c6-656">IS_UPDATABLE</span></span>|<span data-ttu-id="669c6-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-657">Boolean</span></span>|  
|<span data-ttu-id="669c6-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="669c6-658">DESCRIPTION</span></span>|<span data-ttu-id="669c6-659">String</span><span class="sxs-lookup"><span data-stu-id="669c6-659">String</span></span>|  
|<span data-ttu-id="669c6-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="669c6-660">DATE_CREATED</span></span>|<span data-ttu-id="669c6-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-661">DateTime</span></span>|  
|<span data-ttu-id="669c6-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="669c6-662">DATE_MODIFIED</span></span>|<span data-ttu-id="669c6-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="669c6-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="669c6-664">索引</span><span class="sxs-lookup"><span data-stu-id="669c6-664">Indexes</span></span>  
  
|<span data-ttu-id="669c6-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="669c6-665">ColumnName</span></span>|<span data-ttu-id="669c6-666">DataType</span><span class="sxs-lookup"><span data-stu-id="669c6-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="669c6-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-667">TABLE_CATALOG</span></span>|<span data-ttu-id="669c6-668">String</span><span class="sxs-lookup"><span data-stu-id="669c6-668">String</span></span>|  
|<span data-ttu-id="669c6-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="669c6-670">String</span><span class="sxs-lookup"><span data-stu-id="669c6-670">String</span></span>|  
|<span data-ttu-id="669c6-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-671">TABLE_NAME</span></span>|<span data-ttu-id="669c6-672">String</span><span class="sxs-lookup"><span data-stu-id="669c6-672">String</span></span>|  
|<span data-ttu-id="669c6-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="669c6-673">INDEX_CATALOG</span></span>|<span data-ttu-id="669c6-674">String</span><span class="sxs-lookup"><span data-stu-id="669c6-674">String</span></span>|  
|<span data-ttu-id="669c6-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="669c6-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="669c6-676">String</span><span class="sxs-lookup"><span data-stu-id="669c6-676">String</span></span>|  
|<span data-ttu-id="669c6-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-677">INDEX_NAME</span></span>|<span data-ttu-id="669c6-678">String</span><span class="sxs-lookup"><span data-stu-id="669c6-678">String</span></span>|  
|<span data-ttu-id="669c6-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="669c6-679">PRIMARY_KEY</span></span>|<span data-ttu-id="669c6-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-680">Boolean</span></span>|  
|<span data-ttu-id="669c6-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="669c6-681">UNIQUE</span></span>|<span data-ttu-id="669c6-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-682">Boolean</span></span>|  
|<span data-ttu-id="669c6-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="669c6-683">CLUSTERED</span></span>|<span data-ttu-id="669c6-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-684">Boolean</span></span>|  
|<span data-ttu-id="669c6-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="669c6-685">TYPE</span></span>|<span data-ttu-id="669c6-686">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-686">Int32</span></span>|  
|<span data-ttu-id="669c6-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="669c6-687">FILL_FACTOR</span></span>|<span data-ttu-id="669c6-688">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-688">Int32</span></span>|  
|<span data-ttu-id="669c6-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="669c6-689">INITIAL_SIZE</span></span>|<span data-ttu-id="669c6-690">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-690">Int32</span></span>|  
|<span data-ttu-id="669c6-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="669c6-691">NULLS</span></span>|<span data-ttu-id="669c6-692">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-692">Int32</span></span>|  
|<span data-ttu-id="669c6-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="669c6-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="669c6-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-694">Boolean</span></span>|  
|<span data-ttu-id="669c6-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="669c6-695">AUTO_UPDATE</span></span>|<span data-ttu-id="669c6-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-696">Boolean</span></span>|  
|<span data-ttu-id="669c6-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="669c6-697">NULL_COLLATION</span></span>|<span data-ttu-id="669c6-698">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-698">Int32</span></span>|  
|<span data-ttu-id="669c6-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="669c6-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="669c6-700">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-700">Int64</span></span>|  
|<span data-ttu-id="669c6-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="669c6-701">COLUMN_NAME</span></span>|<span data-ttu-id="669c6-702">String</span><span class="sxs-lookup"><span data-stu-id="669c6-702">String</span></span>|  
|<span data-ttu-id="669c6-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="669c6-703">COLUMN_GUID</span></span>|<span data-ttu-id="669c6-704">Guid</span><span class="sxs-lookup"><span data-stu-id="669c6-704">Guid</span></span>|  
|<span data-ttu-id="669c6-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="669c6-705">COLUMN_PROPID</span></span>|<span data-ttu-id="669c6-706">Int64</span><span class="sxs-lookup"><span data-stu-id="669c6-706">Int64</span></span>|  
|<span data-ttu-id="669c6-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="669c6-707">COLLATION</span></span>|<span data-ttu-id="669c6-708">Int16</span><span class="sxs-lookup"><span data-stu-id="669c6-708">Int16</span></span>|  
|<span data-ttu-id="669c6-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="669c6-709">CARDINALITY</span></span>|<span data-ttu-id="669c6-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="669c6-710">Decimal</span></span>|  
|<span data-ttu-id="669c6-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="669c6-711">PAGES</span></span>|<span data-ttu-id="669c6-712">Int32</span><span class="sxs-lookup"><span data-stu-id="669c6-712">Int32</span></span>|  
|<span data-ttu-id="669c6-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="669c6-713">FILTER_CONDITION</span></span>|<span data-ttu-id="669c6-714">String</span><span class="sxs-lookup"><span data-stu-id="669c6-714">String</span></span>|  
|<span data-ttu-id="669c6-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="669c6-715">INTEGRATED</span></span>|<span data-ttu-id="669c6-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="669c6-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="669c6-717">另請參閱</span><span class="sxs-lookup"><span data-stu-id="669c6-717">See also</span></span>

- [<span data-ttu-id="669c6-718">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="669c6-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
