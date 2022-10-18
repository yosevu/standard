---
sidebar_position: 1
---
# Define different variables for received and expected values in assertions

When writing assertions in [[Testing]] (TODO alias: tests), do not use the same variable reference as both the received and the expected value. This is because you may accidentally assert that a reference to a value is equal to itself. It can also make the test [[Readability]] (TODO alias: hard to understand) by obscuring what is happening in the test and cause unexpected failures. For example, if the reference value is changed unexpectedly.

Do this:
```typescript
describe('updateQuality', () => {
  describe('Aged Brie', () => {
    it('increases Aged Brie's quality by one unit per day', () => {
      // Arrange
      const agedBrie =  { name: 'Aged Brie', sellIn: 2, quality: 0 };

      // Define a static expected value.
      const expected =  { name: 'Aged Brie', sellIn: 2, quality: 1 };

      // Define a different received value
      const received = updateQuality(agedBrie);

      // Assert that the received value is equal to the expected value.
      expect(received).toEqual(expected);
    });
  });
});
```

Don't do this:
```typescript
describe('updateQuality', () => {
  describe('Aged Brie', () => {
    it('increases Aged Brie's quality by one unit per day', () => {
      let agedBrie =  { name: 'Aged Brie', sellIn: 2, quality: 0 };
      agedBrie = updateQuality(agedBrie);

      // Don't assert that the updated value is equal to itself.
      expect(agedBrie).toEqual(agedBrie);
    });
  });
});
```

This is a easy mistake to make with mocks.
