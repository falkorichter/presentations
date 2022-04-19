combine

# collect

https://github.com/CombineCommunity/rxswift-to-combine-cheatsheet 

```
func testShouldStartWithLoadingState() throws {
        mockRestClient.expectedResponses = [mockPaymentSession(), mockPaymentProfiles]
        sut.refreshPaymentSelection { _ in }
        let states = try awaitPublisher(sut.state
                                            .collect(2)
                                            .first())
        XCTAssert(try XCTUnwrap(states.first?.isLoading))
    }
```

collect 2 and emit them as array
first of this array

https://developer.apple.com/documentation/combine/deferred/collect()/
and 
https://developer.apple.com/documentation/combine/deferred/collect(_:)

https://valueaddedprogramming.com/2018/10/29/rxjava-operators-collect/