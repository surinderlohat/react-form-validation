# React Form validation

Form validation solution for react JS, super easy to use and can handel all the major user cases.
##### Based on the React hooks and reactive programing.
#### No extra dependencies pure react js code & lightweight.

## Features
1. Easy validations solution for react js pure react js no extra dependency.
2. Regex validations.
3. Custom validations.
4. Email validations.
5. Many useful form helping methods i.e hasError, hasChanges, isTouched, getValues, getErrors.
6. Easy to configure.
7. Nested form fields validations.
8. Dynamic add/remove fields.

## Installation
```sh
npm install @surinderlohat/react-form-validation
or
yarn add @surinderlohat/react-form-validation
```
## API Documentation
https://surinderlohat.github.io/react-form-validation/

### Form Helping Methods
#### Note: all methods are available like: form.onSubmit()

| Method | PARAMS| DESCRIPTION |
| ------ | ------ |------ |
| resetToDefault |No | Reset form state to default All fields will be reset to the default state |
| getField | fieldKey i.e name or user.name if nested field | Return the specific field instance |
| getChangedFields | No | Return fields with initial value and changed value |
| clearForm | No | Clear form values and all nested child's |
| onSubmit | No | Return from values and error state |


### Form Getters
| Name | RETURN Type | RETURN VALUE |
| ------ | ------ |------ |
| getValues | object | Return form values in same order we have pass |
| getErrors | object | Display all errors for each nested field |
| hasChanges | boolean | Return true if any field has changes |


### Field Methods
| Method | TYPE | RETURN VALUE | 
| ------ | ------ | ------ |
| hasChanges | Getter | Return field state i.e it's changed or not |
| hasError | Getter | Return error state of the specific field |
| isTouched | Getter | if field is touched or not
| errorMessage| Getter| Return error message for current field from |
| setValue | Function | Set value of specific field |
| getValue | Function | Get value of specific field |
| setRules | (newRules: Rules) | Update field rules on the fly |
| setError | Function | Set custom error message on specific field |
| showErrors | Function | Show error without touching the fields |
### Rules 
``` sh
Rules 
    /* Used to identify which rule we are going to use for a field*/
    rule: 'min' | 'max' | 'required' | 'same' | 'email' | 'regex' | 'custom' | 'between' | 'range';
    /* Rule value used to provide value in rule i.e for min:2 max:10 rule value ruleValue will be ruleValue:2 or 5 
    ruleValue?: any;
    /* Used to provide custom message for each rule */
    message?: string;
    /* For special cases if we need custom validation then this method will help */
    validation?: (field: IField, form?: ReactForm) => string;
```

## How to use
```sh
import { IFieldObject, useReactForm } from '@surinderlohat/react-form-validation';
import FormField from '../FormField/FormField';
import { Box, Typography, Button, Paper } from '@mui/material';
import { FC } from 'react';

// Fields Rules
const field: IFieldObject = {
  name: {
    label: 'User Name',
    placeholder: 'Enter your Name',
    rules: [{ rule: 'required' }],
  },
  email: {
    label: 'Email',
    placeholder: 'Enter your email',
    rules: [{ rule: 'email', message: 'Email is not valid' }],
  },
  password: {
    label: 'Password',
    rules: [{ rule: 'required', message: 'This field is required' }],
  },
  confirmPassword: {
    label: 'Confirm Password',
    rules: [{ rule: 'required' }, { rule: 'same', ruleValue: 'password', message: 'Should be same as Password' }],
  },
};

const BasicExample: FC = () => {
  const form = useReactForm(field);
  return (
    <Box sx={{ display: 'flex', justifyContent: 'center' }}>
      <Paper sx={{ width: '350px', padding: '15px', display: 'grid', gridGap: '15px' }}>
        <Typography variant="h5">Basic Signup Validations</Typography>
        {Object.keys(field).map(key => (
          <FormField key={key} field={form.getField(key)} />
        ))}
        <Button onClick={() => console.log(form.getValues())} disabled={form.hasError} variant="contained">
          Save Changes
        </Button>
        <Typography>Has Changes: {`${form.hasChanges}`}</Typography>
        <Typography>Has hasError: {`${form.hasError}`}</Typography>
        <Button onClick={() => form.showErrors()} variant="contained">
          Show Errors
        </Button>
      </Paper>
    </Box>
  );
};

export default BasicExample;

```

## Live working Examples
Coming Soon...

Like this package ? show some love by start this repo

For more packages like this please checkout: https://github.com/surinderlohat

## License
MIT **Free Software!**
