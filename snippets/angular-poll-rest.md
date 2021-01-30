To call the http request every 10 seconds:

``` typescript
 timerSubscription: Subscription;
 
 ngOnInit(): void {
      // timer(0, 10000) call the function immediately and every 10 seconds
      this.timerSubscription = timer(0, 10000).pipe(
      map(() => {
        this.loadData(); // load data contains the http request
      })
    ).subscribe();
    }
    
     ngOnDestroy(): void {
    this.timerSubscription.unsubscribe();
  }
```
