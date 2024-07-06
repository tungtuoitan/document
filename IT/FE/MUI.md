# các package

## mui/material

- triển khai Google Material Design, tức cung cấp UI component
<!--link về Google material design: https://m2.material.io/design/introduction -->

## emotion/react

- cho phép viết css trong js, jsx

## emotion/style
- là API trong emotion/react
- dùng để tạo component có style đi kèm

import { css } from '@emotion/react';
import styled from '@emotion/styled';

const StyledDiv = styled.div`
  background-color: #f0f0f0;
  padding: 20px;
  border-radius: 4px;
`;