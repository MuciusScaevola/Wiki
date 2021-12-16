Consider the elements one at a time, inserting each into its proper place amonge those already considered (keeping them sorted).

```c
void insertion_sort(Item a[], int l, int r)
{
    int i;
    
    for(i = r; i > l; i--) compexch(a[i - 1], a[i]);        // Put smallest elem
    
    for(i = l + 2; i <= r; i++)
    {
        int j = i;
        Item v = a[i];
        while(less(v, a[j - 1]))
        {
            a[j] = a[j - 1];
            j--;
        }
        a[j] = v;
    }
}
```

This implementation first puts the smallest element in the first position to act as sentinel.
