# Cash  Register

{% code title="CashRegister.js" overflow="wrap" lineNumbers="true" %}
```javascript
class CashRegister {
  constructor(cashInRegister) {
    this.cashInRegister = cashInRegister;
  }

  static currencyUnit = new Map([
    ['PENNY', 0.01],
    ['NICKEL', 0.05],
    ['DIME', 0.1],
    ['QUARTER', 0.25],
    ['ONE', 1],
    ['FIVE', 5],
    ['TEN', 10],
    ['TWENTY', 20],
    ['HUNDRED', 100],
  ]);

  calculateChange(changeAmount) {
    const changes = [];

    for (const [unit, value] of this.cashInRegister) {
      const unitCashValue = CashRegister.currencyUnit.get(unit) * 100;

      if (changeAmount >= unitCashValue) {
        const maxNumberOfUnit = Math.floor(changeAmount / unitCashValue);
        const maxChangeOfUnit = maxNumberOfUnit * unitCashValue;

        if (value * 100 >= maxChangeOfUnit) {
          changes.push([unit, maxChangeOfUnit / 100]);
          changeAmount -= maxChangeOfUnit;
        } else {
          changes.push([unit, value]);
          changeAmount -= value * 100;
        }
      }
    }

    return changes;
  }

  change(price, cash) {
    const changeAmount = cash * 100 - price * 100;

    if (this.checkRegisterTotal() === changeAmount) {
      return { status: 'CLOSED', changes: this.cashInRegister };
    }

    if (this.checkRegisterTotal() < changeAmount) {
      return { status: 'INSUFFICIENT_FUNDS', changes: [] };
    }

    const changes = this.calculateChange(changeAmount / 100);

    if (changes.reduce((acc, [unit, value]) => acc + value * 100, 0) < changeAmount) {
      return { status: 'INSUFFICIENT_FUNDS', changes: [] };
    }

    return { status: 'OPEN', changes };
  }

  checkRegisterTotal() {
    return this.cashInRegister.reduce((acc, [_unit, value]) => acc + value * 100, 0);
  }
}

module.exports = CashRegister;
```
{% endcode %}

**Example usage**

```javascript
const initialCashInRegister = [
  ['PENNY', 1.01],
  ['NICKEL', 2.05],
  ['DIME', 3.1],
  ['QUARTER', 4.25],
  ['ONE', 90],
  ['FIVE', 55],
  ['TEN', 20],
  ['TWENTY', 60],
  ['HUNDRED', 100]
];

const register = new CashRegister(initialCashInRegister);

const price = 19.5;
const cash = 20;

const changeResult = register.change(price, cash);
console.log(changeResult); //{ status: 'OPEN', changes: [ [ 'QUARTER', 0.5 ] ] }

```
