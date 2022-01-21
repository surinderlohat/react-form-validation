# Lohat React Form validation

Form validation solution for react JS, super easy to use and can handel all the major user cases.
##### Based on the React hooks and reactive programing.
#### No extra dependencies pure react js code & lightweight.

## Featuers
1. Easy validations solution for react js.
2. Regex validations.
3. Custom validations.
4. Email validations.
5. Many useful form helping methods i.e hasError, hasChanges, isTouched, getValues, getErrors.
6. Easy to configure.
7. Support complex user cases.
8. Nested form fields validations.
9. Dynamic add/remove fields.
10. Open source Free to use.

## Installation
```sh
npm install @surinderlohat/lohat-react-form-validation
or
yarn add @surinderlohat/lohat-react-form-validation
```
## API Documentation
https://surinderlohat.github.io/lohat-react-form-validation/

### Form Helping Methods
#### Note: all methods are available like: form.onSubmit()

| Method | PARAMS| DESCRIPTION |
| ------ | ------ |------ |
| resetToDefault |No | Reset form state to default All fields will be reset to the default state |
| getField | fieldKey i.e name or user.name if nested field | Return the specific field instance |
| getChangedFields | No | Return fields with initial value and changed value |
| clearForm | No | Clear form values and all nested childs |
| onSubmit | No | Return from values and error state |


### Form Helping Getter
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
| errorMessage|Getter| Return error message for current field |
| setValue |Function| Set value of specific field 

## How to use
```sh
import { FieldObject, useLohatForm } from '@surinderlohat/lohat-react-form-validation';
const fields: FieldObject = {
  firstName: {
    label: 'First Name',
    value: 'Surinder',
    rules: {
      required: true,
      min: 2,
      max: 10,
    },
  },
 lastName: {
    label: 'Last Name',
    value: 'Singh',
    rules: {
      required: true,
      min: 2,
      max: 10,
    },
  },
  email: {
    label: 'Email',
    value: 'test@domain.com',
    rules: {
      isEmail: true,
      min: 2,
      max: 10,
    },
  },
};

function FormValidation() {
  const form = useLohatForm(fields);
  return (
    <div className="App">
      <form>
        <FormField field={form.getField('firstName')} />
        <FormField field={form.getField('lastName')} />
        <FormField field={form.getField('email')} />
        <Button onClick={()=>form.getValues()}>
        Save Changes
        </Button>
      </form>
    </div>
  );
}

function FormField({ field }: Props) {
  return (
    <TextField
      {...field.bind()} // find input methods to input i.e onChange, onBlur, onFocus
      label={field.starLabel}
      error={field.hasError}
      helperText={field.errorMessage}
      variant="filled"
    />
  );
}

```

## Live working Examples

#### Basic validation with email validation
https://codesandbox.io/s/lohat-react-form-validation-o216l

#### Setup custom error message using form instance
https://codesandbox.io/s/lohat-react-form-validation-forked-ctejo

#### Nested form fields : Example incule getValues() and getErrors() for specific nested field

https://codesandbox.io/s/lohat-react-form-validation-forked-tzmn3



## License
MIT **Free Software!**
