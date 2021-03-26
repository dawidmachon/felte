---
section: Validators
subsections:
  - Using Yup
---

## Validators

If you use third party libraries for validation you might have found yourself needing to transform the output from said validation library to the form library you're using (unless the form library supports it natively or provides its own built-in alternative). In order to not reinvent the wheel, and to make life easier for you, we provide some official `validators` which are, basically, adapters for popular validation libraries.

If a validation library you use is not supported, feel free to [open an issue](https://github.com/pablo-abc/felte/issues), we would like to support the most used ones! You may also build your own validation package.

### Using Yup

[Yup](https://github.com/jquense/yup) is a really popular validation library. For this reason we've created [`@felte/validator-yup`](https://github.com/pablo-abc/felte/tree/main/packages/validator-yup). An official package to handle validation with Yup. To use it you'll need both `@felte/validator-yup` and `yup`.

```sh
npm install --save @felte/validator-yup yup

# Or, if you use yarn

yarn add @felte/validator-yup yup
```

It's usage would look something like:

```javascript
import { validator } from '@felte/validator-yup';
import * as yup from 'yup';

const schema = yup.object({
  email: yup.string().email().required(),
  password: yup.string().required(),
});

const { form } = createForm({
  // ...
  extend: validator, // OR `extend: [validator],`
  validateSchema: schema,
  // ...
});
```