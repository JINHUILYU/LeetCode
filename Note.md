# Notes
## 二分查找
在二分查找中，`while left < right` 和 `while left <= right` 的选择，以及 `left` 和 `right` 的更新方式，取决于搜索区间的定义和具体需求。

**1. 循环条件：`while left < right` vs `while left <= right`**

- **`while left <= right`：**
  - 适用于**左闭右闭**区间，即区间包含左右端点。
  - 在每次迭代中，`right` 被更新为 `mid - 1`，确保不会重复访问。
  - 例如，查找目标值的位置时，使用 `while left <= right`，并在循环内将 `right` 更新为 `mid - 1`。
  
- **`while left < right`：**
  - 适用于**左闭右开**区间，即区间包含左端点但不包含右端点。
  - 在每次迭代中，`right` 被更新为 `mid`，因此 `right` 不会被重复访问。
  - 例如，查找第一个大于等于目标值的位置时，使用 `while left < right`，并在循环内将 `right` 更新为 `mid`。

**2. 更新 `left` 和 `right` 时，`mid` 的计算方式**

- **`mid = (left + right) // 2`：**
  - 适用于**左闭右闭**区间。
  - 在每次迭代中，`left` 被更新为 `mid + 1`，`right` 被更新为 `mid - 1`。
  - 例如，查找目标值的位置时，使用 `while left <= right`，并在循环内将 `left` 更新为 `mid + 1`，`right` 更新为 `mid - 1`。

- **`mid = (left + right + 1) // 2`：**
  - 适用于**左闭右开**区间。
  - 在每次迭代中，`left` 被更新为 `mid`，`right` 被更新为 `mid - 1`。
  - 例如，查找第一个大于等于目标值的位置时，使用 `while left < right`，并在循环内将 `right` 更新为 `mid`。

**3. 为什么有时直接更新 `left` 或 `right` 为 `mid`，有时更新为 `mid + 1` 或 `mid - 1`**

- **直接更新为 `mid`：**
  - 适用于需要在下一次迭代中重新考虑当前 `mid` 的情况。
  - 例如，在查找第一个大于等于目标值的位置时，可能需要重新考虑当前 `mid`，因此将 `right` 更新为 `mid`。

- **更新为 `mid + 1` 或 `mid - 1`：**
  - 适用于确定当前 `mid` 不可能是目标值，且不需要重新考虑的情况。
  - 例如，在查找目标值的位置时，如果当前 `mid` 小于目标值，则将 `left` 更新为 `mid + 1`，如果当前 `mid` 大于目标值，则将 `right` 更新为 `mid - 1`。

总之，二分查找的具体实现取决于搜索区间的定义和具体需求。 理解这些细节有助于正确地实现二分查找算法。