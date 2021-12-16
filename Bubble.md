Keep passing through the file, exchanging adjacent elements that are out of order until the file is sorted.

```c
void bubble_sort(Item a[], int l, int r)
{
    int i, j;
    
    for(i = l; i < r; i++)
    {
        for(j = r; j > i; j--)
        {
            compexch(a[j - 1], a[j]);
        }
    }
}
```
