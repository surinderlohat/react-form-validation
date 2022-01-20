# Lohat Form validation

Lohat Form validation is a form validation solution for react JS, it's super easy to use, Can configure to match all the major user cases.
This library is based on the react hooks and reactive programing. 
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
npm install @surinderlohat/lohat-from-validation
yarn add @surinderlohat/lohat-from-validation
```
## API Documentation
https://surinderlohat.github.io/lohat-from-validation/

### Form Helping Methods
#### Note: all methods are available like: form.onSubmit()

| Method | PARAMS| RETURN VALUE |
| ------ | ------ | ------ |
| onSubmit | No | Return from values and error state |
| getValues | No | Return form values in same order we have pass |
| getErrors | No | Display all errors for each nested field |
| resetToDefault |No |Reset form state to default All fields will be reset to the default state |
| getField | fieldKey |used to get the specific field from the form|

### Field Methods
 Note: we can get any specific field using form.getField('userName')
all methods are available like: form.getField('userName').hasChanges

| Method | TYPE | RETURN VALUE | 
| ------ | ------ | ------ |
| hasChanges | Getter | Return field state i.e it's changed or not |
| hasError | Getter | Return error state of the specific field |
| errorMessage|Getter| Return error message for current field |
| setValue |Function| Set value of specific field 

## How to use
```sh
import { FieldObject, useLohatForm } from '@surinderlohat/lohat-from-validation';
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
      label={field.startLabel}
      error={field.hasError}
      helperText={field.errorMessage}
      variant="filled"
    />
  );
}

```

## Live working Examples

### Basic validation
https://codesandbox.io/embed/sleepy-napier-ci2lg



## License
MIT **Free Software!**
