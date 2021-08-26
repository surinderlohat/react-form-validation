# Lohat Form validation

Lohat Form validation is a tool for easy form validations based on the react hooks and reactive programing.

## Installation
```sh
npm install @surinderlohat/lohat-from-validation
yarn add @surinderlohat/lohat-from-validation
```
### Form Helping Methods
#### Note: all methods are available like: form.onSubmit()

| Method | PARAMS| RETURN VALUE |
| ------ | ------ | ------ |
| onSubmit | No | Return from values and error state |
| errorMessages | No | Display all errors from the fields |
| resetToDefault |No |Reset form state to default All fields will be reset to the default state |
| getField | fieldKey |used to get the specific field from the form|

### Field Methods
 Note: we can get any specific field using form.getField('userName')
all methods are available like: form.getField('userName').hasChanges
| Method | TYPE | RETURN VALUE | 
| ------ | ------ | ------ |
| hasChanges | Getter | Return field state i.e it's changed or not |
| hasError | Getter | Return error state of the specific field |
| errorMessage|Getter| Return error message for current field|
| setValue |Function| Set value of specific field 

## How to use
```sh
import { FieldObject, useLohatForm } from '@surinderlohat/lohat-from-validation';
const field: FieldObject = {
  userName: {
    label: 'UserName',
    value: '123',
    rules: {
      required: true,
      regExp: /^[0-9]+$/,
      min: 2,
      max: 10,
    },
  },
  email: {
    label: 'Email',
    value: 'abc@gmail.com',
  },
};

function FormValidation() {
  const form = useLohatForm(field);
  return (
    <div className="App">
      <form>
        <FormField field={form.getField('userName')} />
        <FormField field={form.getField('email')} />
      </form>
    </div>
  );
}

function FormField({ field }: Props) {
  return (
    <div>
      <label>{field.label}</label>
      <input {...field.bind()}></input>
      <p> errorMessage{'' + field.errorMessage}</p>
    </div>
  );
}

```

## Live working Link
https://codesandbox.io/embed/sleepy-napier-ci2lg

## API Documentation
https://surinderlohat.github.io/lohat-from-validation/

## License
MIT **Free Software!**
