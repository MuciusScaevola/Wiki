First, find the smallest element in the array, and exchange it with the element in the first position. Then, find the second smallest
and exchange it with the element in the second position. Continue until the array sorted.

```c
void selection_sort(Item a[], int l, int r)
{
    int i, j;
    
    for(i = l; i < r; i++)
    {
        int min = i;
        for(j = i + 1; j <= r; j++)
        {
            if(less(a[j], a[min])) min = j;
        }
        exch(a[i], a[min]);
    }
}
```
