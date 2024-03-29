# Navbar 개발



```react
// Navbar.tsx

import {
  NavbarBackground,
  NavbarItemWrapper,
  NavbarLinkWrappper,
  NavbarPurgaeLink,
  NavbarLink,
  NavbarLoginWrapper,
  NavbarHamburger,
  NavbarLoginLink,
} from "./Navbar.styled";
import { Outlet } from "react-router";
import { useState, Fragment, useEffect } from "react";

const Navbar = () => {
  const [ScrollY, setHeaderColor] = useState(0);
  const [HeaderStatus, setHeaderStatus] = useState(false);

  const Navbar = document.getElementById("navbar");
  const NavbarHeight: any = Navbar?.getBoundingClientRect().height;

  const handleColor = () => {
    setHeaderColor(window.pageYOffset);
    ScrollY > NavbarHeight ? setHeaderStatus(true) : setHeaderStatus(false);
  };

  useEffect(() => {
    const watch = () => {
      window.addEventListener("scroll", handleColor);
    };
    handleColor();
    watch();
    return () => {
      window.removeEventListener("scroll", handleColor);
    };
  });

  const [menuToggle, setMenuToggle] = useState<boolean>(false);

  return (
    <Fragment>
      <NavbarBackground opacity={!HeaderStatus ? "1" : "0"} id="navbar">
        <NavbarItemWrapper>
          <NavbarHamburger onClick={() => (menuToggle ? setMenuToggle(false) : setMenuToggle(true))}>
            <div className="material-icons">menu</div>
          </NavbarHamburger>
          <NavbarLinkWrappper display={!menuToggle ? "none" : "flex"}>
            <NavbarPurgaeLink to="/main">푸르게</NavbarPurgaeLink>
            <NavbarLink to="/game">게임</NavbarLink>
            <NavbarLink to="/ranking">랭킹</NavbarLink>
            <NavbarLink to="/donate">기부</NavbarLink>
            <NavbarLink to="/faq">자주 묻는 질문</NavbarLink>
          </NavbarLinkWrappper>
          <NavbarLoginWrapper>
            <NavbarLoginLink to="/login">로그인</NavbarLoginLink>
          </NavbarLoginWrapper>
        </NavbarItemWrapper>
      </NavbarBackground>
      <Outlet />
    </Fragment>
  );
};

export default Navbar;
```



```react
// Navbar.styled.ts

import { NavLink } from "react-router-dom";
import { styled } from "../../styles/theme";

export const NavbarBackground = styled.div<{ opacity: string }>`
  display: flex;
  position: fixed;
  flex-direction: row;
  align-items: center;
  max-width: 100%;
  height: 4rem;
  width: ${({ theme }) => theme.sizes.pc};
  padding: 0rem 1.5rem;
  gap: 10.625rem;
  background-image: linear-gradient(350deg, #666af6, #5f6bff, #5299ff, #1ec5ff);
  opacity: ${(props) => props.opacity};
  box-shadow: ${({ theme }) => theme.shadows.shadow600};
  transition: opacity 0.5s linear;
  &:hover {
    opacity: 1;
  }
`;

export const NavbarItemWrapper = styled.div`
  ${({ theme }) => theme.mixins.flexBox("row", "center", "space-between")};
  width: 117rem;
  padding: 0rem;
`;

export const NavbarLinkWrappper = styled.div<{ display: string }>`
  ${({ theme }) => theme.mixins.flexBox()}
  padding: 0rem;
  gap: 3rem;
  @media screen and (max-width: 768px) {
    display: ${(props) => props.display};
    position: fixed;
    flex-direction: column;
    align-items: flex-start;
    top: 4rem;
    left: 0rem;
    padding: 1.5rem 3.125rem;
    gap: 2rem;
    background-color: ${({ theme }) => theme.colors.white};
  }
`;

export const NavbarLoginWrapper = styled.div`
  ${({ theme }) => theme.mixins.flexBox()}
  padding: 0rem;
  gap: 1.25rem;
`;

export const NavbarPurgaeLink = styled(NavLink)`
  ${({ theme }) => theme.mixins.font("2rem", "700")};
  color: ${({ theme }) => theme.colors.white};
  text-decoration: none;
  @media screen and (max-width: 768px) {
    ${({ theme }) => theme.mixins.font("1.25rem", "500")};
    color: ${({ theme }) => theme.colors.primary500p};
    &:hover {
      color: ${({ theme }) => theme.colors.primary500p};
      ${({ theme }) => theme.mixins.font("1.25rem", "700")};
    }
  }
`;

export const NavbarLink = styled(NavLink)`
  ${({ theme }) => theme.mixins.font("1.25rem", "500")};
  color: ${({ theme }) => theme.colors.white};
  letter-spacing: 0.075rem;
  text-decoration: none;
  &.active {
    color: ${({ theme }) => theme.colors.white};
    ${({ theme }) => theme.mixins.font("1.25rem", "700")};
  }
  &:hover {
    color: ${({ theme }) => theme.colors.white};
    ${({ theme }) => theme.mixins.font("1.25rem", "700")};
  }
  @media screen and (max-width: 768px) {
    color: ${({ theme }) => theme.colors.primary500p};
    &:hover {
      color: ${({ theme }) => theme.colors.primary500p};
    }
  }
`;

export const NavbarLoginLink = styled(NavLink)`
  ${({ theme }) => theme.mixins.font("1.25rem", "500")};
  color: ${({ theme }) => theme.colors.white};
  letter-spacing: 0.075rem;
  text-decoration: none;
  &.active {
    color: ${({ theme }) => theme.colors.white};
    ${({ theme }) => theme.mixins.font("1.25rem", "700")};
  }
  &:hover {
    color: ${({ theme }) => theme.colors.white};
    ${({ theme }) => theme.mixins.font("1.25rem", "700")};
  }
`;

export const NavbarHamburger = styled.button`
  display: none;
  width: 1.5rem;
  height: 1.5rem;
  color: ${({ theme }) => theme.colors.white};
  @media screen and (max-width: 768px) {
    display: flex;
  }
`;
```

